---
layout: post
title: How to make a 3rd person controller shoot game using Unity 3D (6-6)
date: 2016-12-5
categories: article unity game shooter tutorial
---
<!--more-->

## 6 Make it complete

- Find source project in [Shooter](https://github.com/hanhonglei/Shooter) 

### Optimize game framework

Use inherit of `C#` class to manage characters and items in the game scene. `Enemy` and `Player` are all inherited from `Actor`. `Actor` can have weapons, fire, be damaged, die. `Bullet` and `Weapon` are all inherited from `Item`. `Item` can be picked up or used, initialized randomly, used by enemy or the player.

Use a game manager to handle global staff.
- Drop item system
- Record some game information
- Notify UI to display particular information

Set a `text UI` to display game information.

### Item generate system

When a item drop order is triggered
- When an enemy dies

There is a particular probability to drop an item
- It has a drop probability parameter

The Manager takes over the generate process.

It use a strategy to decide which level item should be generated.

Then use item collection in this level to finally generate a random item inside it.

### Item drop system

Write a script named EnemyDropItemProc that would be grabbed into an enemy or other item-droppable objects

There are some adjustable parameters in this class:

- **Enemy Level** The enemies can be divided into several levels, there are 5 levels in the Shooter Example. It more likes that the enemy will drop the same level items when they killed by the player. Particular level means special.
- **Level Manager** The pointer to the level manager in the scene. It will handle all item drop functions.
- **Drop Item Per** The probability of the enemy to drop items when is killed.

**EnemyDropItemProc**
{% highlight csharp %}
public ItemLevel enemyLevel = ItemLevel.Level1;
    public LevelManager levelManager = null;
    public float dropItemPer = 0.1f; 
	// Use this for initialization
	void Start () {
        if (!levelManager)
        {
            levelManager = GameObject.FindGameObjectWithTag(Tags.gameController).GetComponent<LevelManager>();
        }	
	}
    public Item DropItem()
    {
        if (Random.Range(0f, 1f) < dropItemPer)
        {
            Debug.Log("Drop an item");
            return levelManager.GenerateRandomItem(transform);
        }
        return null;
}
{% endhighlight %}

Function `DropItem` will be called when the enemy is killed by the player

It would be called in `Die` function of `Enemy` script like this:

{% highlight csharp %}
protected override void Die()
    {
        SendMessage("DropItem");
        lm.killEnemyNum++;
        GameObject.Destroy(gameObject);
    }
{% endhighlight %}

In script `LevelManager`, the function `GenerateRandomItem`, that will handle all random generate items process

It can generate random items based on the enemy item percentage and level

All droppable items would be managed in a script named `ItemsCollection`, it can return a random, use function `GenerateRandomLevelItem`, item from a particular item level list

![]({{site.url}}/Images/shooter/image28.png){:height="300px"}

This is the end of this tutorial.

More details, please visit the project [here](https://github.com/hanhonglei/Shooter) 


<script>
  (function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
  (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
  m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
  })(window,document,'script','https://www.google-analytics.com/analytics.js','ga');

  ga('create', 'UA-85986843-1', 'auto');
  ga('send', 'pageview');

</script>