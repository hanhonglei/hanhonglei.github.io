---
layout: post
title: How to make a 3rd person controller shoot game using Unity 3D (5-6)
date: 2016-12-5
categories: article unity game shooter tutorial
---
<!--more-->

## 5 Weapon and other advanced game functions

- Find source project Tutorial_4_Upgrade in [Shooter](https://github.com/hanhonglei/Shooter) 

### Weapon compositions

**Gun + bullet**

- Gun: shoot frequency, ammo, fire direction
- Bullet: damage, speed, damage type

**Player to control it**

- Player script to handle weapon change, fire, and pick up items

### Weapon

`lastShootTime` and `freezeTime` to implement weapon freeze time。

{% highlight csharp %}
 public void Fire(Vector3 target)
    {
        if (lastShootTime < freezeTime)
            return;
        Vector3 dir = target - bulletPos.position;
        Vector3 xyProject = Vector3.ProjectOnPlane(dir, Vector3.up);
        if (num <= 0)
            return;
        Vector3 bulletStartPos = bulletPos.position;
        bulletStartPos.y = 1;
        GameObject g = (GameObject)GameObject.Instantiate(bullet, bulletStartPos, Quaternion.FromToRotation(Vector3.forward, xyProject.normalized));
       num--;
        lastShootTime = 0f;
    }
{% endhighlight %}

### Calculate fire direction

Calculate fire direction based on mouse position

{% highlight csharp %}
 if (Input.GetButton("Fire1"))
        {
            Ray ray = Camera.main.ScreenPointToRay(Input.mousePosition);
            float enter = 0.0f;
            Plane firePlane = new Plane(Vector3.up, weaponPos.position);
            if (firePlane.Raycast(ray, out enter))
            {
                desPos = ray.GetPoint(enter);
            }
            Fire(desPos);
        }
{% endhighlight %}

### Bullet

In `Update` to let bullet move in a particular speed. Set bullet game object collider as `trigger` type. When collider with others, then check if cause damage.

![Set as trigger]({{site.url}}/Images/shooter/image21.png){:height="300px"}

{% highlight csharp %}
 public void Update()
    {
        if (bMove)
            rb.MovePosition(transform.position + transform.forward * speed * Time.deltaTime);
    }

    public void OnTriggerEnter(Collider other)
    {
        switch (other.tag)
        {
            case Tags.obstacle:
                bMove = false;
                break;
            case Tags.enemy:
                break;
            default:
                return;
        }
        BeginDamage(other);
    }
{% endhighlight %}

### Grab a gun

Characters can equip a particular weapon.

{% highlight csharp %}
 void Start()
    {
        if (!weaponPos)
            weaponPos = gameObject.transform;
        for (int i = 0; i < weapons.Length; i++)
        {
            weapons[i] = (GameObject)Instantiate(weapons[i], weaponPos.position, Quaternion.identity);
            if (gameObject.tag == Tags.enemy)
                weapons[i].SendMessage("SetAsEnemy", true);
            weapons[i].transform.SetParent(weaponPos);
            //weapons[i].SendMessage("SetUsable", i == currWeapon);
            weapons[i].gameObject.SetActive(i == currWeapon);
        }
    }
{% endhighlight %}

### Cause damage to characters

The bullet from the player will cause damage to enemies, and vice verse. 

Different type of bullet will cause different type of damage. 
- Common bullet will cause instant damage
- Explosion bullet will damage all characters inside the efficient region
- Consistent bullet will cause damage for a while
- Puncture bullet wouldn’t stop when hit a character

### Change weapon

{% highlight csharp %}
 bool NextWeapon(int next)
    {
        weapons[currWeapon].gameObject.SetActive(false);
        currWeapon = Mathf.Abs(currWeapon + next + weapons.Length) % weapons.Length;

        weapons[currWeapon].gameObject.SetActive(true);
        StopFire(); // stop fire when changing to a new weapon
        return true;
    }
{% endhighlight %}

### Use prefabs

![]({{site.url}}/Images/shooter/image22.png){:height="300px"}
![]({{site.url}}/Images/shooter/image23.png){:height="300px"}
![]({{site.url}}/Images/shooter/image24.png){:height="300px"}
![]({{site.url}}/Images/shooter/image25.png){:height="300px"}
![]({{site.url}}/Images/shooter/image26.png){:height="300px"}

### Weapon system logic

Instantiate all possible weapons for every character.

But only one of them is currently useable.
- The others are disable
- When the player pick up weapon, corresponding weapon in its weapon list will become usable

When fire, current weapon will try to instantiate a bullet, then bullet script will take over the following process.
- Enemy will fire at the player
- Player will fire at the direction where the mouse point to

### Set enemy behavior

Set the enemy tag as `Enemy`. Use enemy script to receive damage when shot. When the health of enemy below to 0, die. There is some probability to drop an item.

{% highlight csharp %}
 protected override void Die()
    {
        SendMessage("DropItem");

        lm.killEnemyNum++;

        GameObject.Destroy(gameObject);
    }
{% endhighlight %}

![]({{site.url}}/Images/shooter/image27.png){:height="300px"}

Next turoial please click [Make it complete]({{site.url}}/article/unity/game/shooter/tutorial/2016/12/05/unity-shooter-tutorial-6.html).

More details, please visit the project [here](https://github.com/hanhonglei/Shooter) 


<script>
  (function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
  (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
  m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
  })(window,document,'script','https://www.google-analytics.com/analytics.js','ga');

  ga('create', 'UA-85986843-1', 'auto');
  ga('send', 'pageview');

</script>