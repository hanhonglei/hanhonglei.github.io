---
layout: post
title: A demo shows how to use Leap motion in VR environment based on Unity 3D
date: 2016-10-28
categories: article unity game vr leapmotion
---
<!--more-->

Let your `Unity 3D` game scene run in VR head-mounted glasses is easy. First download all related SDK and Unity resource of particular VR glasses, such as Oculus Rift. Then click the `Virtual Reality Supported` showed in the image below. That’s it.

![]({{site.url}}/Images/LM/image12.png){:height="300px"}

Leap motion can provide figure gesture control function which is always lack in other VR hand controllers.

Here is an [example](https://bitbucket.org/Honglei_Han/leapmotioncontrolvrdemo) for how to integrate Leap motion hand gesture interaction method in a tower-defense game. At first, you should download all Unity related developer resources from Leap motion developer website. And then import these assets packages into your Unity game project.

We first create a terrain and beautify it use tools in the terrain inspector window.

You can use brush to paint out different landforms like this.

![]({{site.url}}/Images/LM/image13.png){:height="300px"}

Paint texture on terrain.

![]({{site.url}}/Images/LM/image14.png){:height="300px"}

Finally, add grass, tree, or other terrain details.

![]({{site.url}}/Images/LM/image15.png){:height="300px"}

Add skybox, or other global effects for your game scene are also not so hard. You can do it like the images below.

![]({{site.url}}/Images/LM/image16.png){:height="300px"}
![]({{site.url}}/Images/LM/image17.png){:height="300px"}

Unity supports 3D model in a very intuitive way. You can grab 3D models into your game project, and then grab them into your game scene.

![]({{site.url}}/Images/LM/image18.png){:height="300px"}

Unity uses `Mecanim` system to control animations in a model. You should always use `Animation Controller` to control the animation clips in a model.

![]({{site.url}}/Images/LM/image19.png){:height="300px"}

It’s time to add AI function to an enemy model. Here the AI is mainly path finding.

![]({{site.url}}/Images/LM/image20.png){:height="300px"}
![]({{site.url}}/Images/LM/image21.png){:height="300px"}

In order to make AI effective, you should add `NavMeshAgent` to AI models like this.

![]({{site.url}}/Images/LM/image22.png){:height="300px"}

It’s time to hit the script, use a script to give them destination. Create an empty game object as the destination.

![]({{site.url}}/Images/LM/image23.png){:height="300px"}

The script can be written like this. Grab this script into the enemies.

{% highlight csharp %}
    public Transform destPoint;                             
    private NavMeshAgent nav;
    void Awake()
    {
        nav = GetComponent<UnityEngine.AI.NavMeshAgent>();  
        if (!nav)
            return;
        Init();
    }
    public void Init()
    {
        nav.SetDestination(destPoint.position);     // set nav destination
    }
{% endhighlight %}

Now, we are moving to Leap motion stuff. Leap motion supports two kinds of methods for hand gesture interaction. The fist is traditional one, the other is VR one. The latter one requires Leap motion sensor stick in the front of the VR glasses. 

In software end, after downloading and importing the Leap motion Unity assets, you can grab the `LMHeadMountedRig` into the game scene as the VR camera and Leap motion hand controller.

![]({{site.url}}/Images/LM/image24.png){:height="80px"}

Configurator hand pool under the `LMHeadMountedRig` game object just grabbed.

![]({{site.url}}/Images/LM/image25.png){:height="300px"}

Add graphic and physical hand models to it, and set model pool to 2 like this.

![]({{site.url}}/Images/LM/image26.png){:height="300px"}

Now, it’s time to do real hand control things. We should add hand gesture event system into `LMHeadMountedRig`.

![]({{site.url}}/Images/LM/image27.png){:height="300px"}

We should follow these steps to make it works.

1.	Create an empty game object
2.	Grab it to graphic right hand as its child
3.	Add `ExtendedFingerDetector` to it
4.	Configure this script component

![]({{site.url}}/Images/LM/image28.png){:height="200px"}
![]({{site.url}}/Images/LM/image29.png){:height="200px"}

We then add a player game object to do interaction. The script hanged in player game object written like this.

{% highlight csharp %}
   public GameObject bullet;
    [SerializeField]
    public Leap.Unity.ExtendedFingerDetector handFinger;
    public void Fire()
    {
        Hand hand;
        hand = handFinger.HandModel.GetLeapHand();
        float[] f = hand.PalmNormal.ToFloatArray();
        Vector3 handNormal = new Vector3(f[0], f[1], f[2]);
        float[] p = hand.PalmPosition.ToFloatArray();
        Vector3 handPos = new Vector3(p[0], p[1], p[2]);
        GameObject.Instantiate(bullet, handPos, Quaternion.FromToRotation(Vector3.forward, handNormal.normalized));
    }
{% endhighlight %}

We should also do some coding to control the bullet.

{% highlight csharp %}
public float speed = 10.0f;
    private Rigidbody rb; // rigid body component of this bullet
    void FixedUpdate()
    {
        rb.MovePosition(transform.position + transform.forward * speed * Time.deltaTime);
    }
    // Use this for initialization
    void Start()
    {
        rb = GetComponent<Rigidbody>();
    }
{% endhighlight %}
 
We can just create a simple bullet prefab.

![]({{site.url}}/Images/LM/image30.png){:height="300px"}

Then we grab the bullet prefab into the player parameter.

![]({{site.url}}/Images/LM/image31.png){:height="300px"}

Finally, the magic thing comes. We use a hand gesture, palm means all fingers extended, to start fire. And use palm direction as fire direction. We can do it even without coding, just use hand event system provided by Leap motion.

![]({{site.url}}/Images/LM/image32.png){:height="300px"}

We can add some UI staff as well.

![]({{site.url}}/Images/LM/image33.png){:height="300px"}
![]({{site.url}}/Images/LM/image34.png){:height="300px"}

Use script to control UI elements.

{% highlight csharp %}
    void Start()
    {
        gameInfo = GameObject.Find("Text").GetComponent<Text>();
    }
    // Update is called once per frame
    void Update()
    {
        gameInfo.text = "Kill enemies:" + "\n" + "Lost enemies:" + "\n"
    + "Weapon:" + "\n" + "Ammo:" ;
    }
{% endhighlight %}

We should also implement some game logics. Such as Bullet collider with enemies, and enemy behaviors.

{% highlight csharp %}
public PlayerFire p;
    public void ShootMe()
    {
        p.killed++;
        Destroy(gameObject);
    }
{% endhighlight %}

Bullet collider behavior can like this.

{% highlight csharp %}
public PlayerFire p;
void OnCollisionEnter(Collision collision)
    {
        if (collision.gameObject.tag == "Enemy")
        {
            EnemyAI eai = collision.gameObject.GetComponent<EnemyAI>();
            eai.ShootMe();
        }        
    }
{% endhighlight %}

![]({{site.url}}/Images/LM/image35.png){:height="300px"}

More details, please visit the demo project [here](https://bitbucket.org/Honglei_Han/leapmotioncontrolvrdemo).


<script>
  (function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
  (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
  m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
  })(window,document,'script','https://www.google-analytics.com/analytics.js','ga');

  ga('create', 'UA-85986843-1', 'auto');
  ga('send', 'pageview');

</script>