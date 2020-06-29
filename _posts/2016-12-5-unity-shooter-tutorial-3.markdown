---
layout: post
title: How to make a 3rd person controller shoot game using Unity 3D (3-6)
date: 2016-12-5
categories: article unity game shooter tutorial
---
<!--more-->

## 3 Actor AI

- Find source project Tutorial_3_AI in [Shooter](https://github.com/hanhonglei/Shooter) 

### Add AI

Add AI to enemies, mainly path finding. Bake navigation first.

![]({{site.url}}/Images/shooter/image15.png){:height="300px"}
![]({{site.url}}/Images/shooter/image16.png){:height="300px"}

Add NavMeshAgent to AI models.

![]({{site.url}}/Images/shooter/image17.png){:height="300px"}

Use script to give them destination.

![]({{site.url}}/Images/shooter/image18.png){:height="300px"}

To avoid polluting complete game script, all script class should be put inside namespace `Tutorial`.

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

Next turoial please click [Enemy patrols]({{site.url}}/article/unity/game/shooter/tutorial/2016/12/05/unity-shooter-tutorial-4.html).

More details, please visit the project [here](https://github.com/hanhonglei/Shooter) 


<script>
  (function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
  (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
  m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
  })(window,document,'script','https://www.google-analytics.com/analytics.js','ga');

  ga('create', 'UA-85986843-1', 'auto');
  ga('send', 'pageview');

</script>