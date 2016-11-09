---
layout: post
title: A simple item drop system of digital games
date: 2016-10-27
categories: article unity game shooter
---
<!--more-->
![]({{site.url}}/Images/49.png)

Write a script named `EnemyDropItemProc` that would be grabbed into an enemy or other item-droppable objects. There are some adjustable parameters in this class:

1. `Enemy Level` The enemies can be divided into several levels, there are 5 levels in the [Shooter Example]( https://github.com/hanhonglei/Shooter). It more likes that the enemy will drop the same level items when they killed by the player. Particular level means special.

2. `Level Manager` The pointer to the level manager in the scene. It will handle all item drop functions.

3. `Drop Item Per` The probability of the enemy to drop items when is killed.

The codes in script named `EnemyDropItemProc` are listed below.

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

Function `DropItem` will be called when the enemy is killed by the player. It would be called in `Die` function of `Enemy` script like this:

{% highlight csharp %}
    protected override void Die()
    {
        SendMessage("DropItem");
        lm.killEnemyNum++;
        GameObject.Destroy(gameObject);
    }
{% endhighlight %}

In script `LevelManager`, the function `GenerateRandomItem` , that will handle all random generate items process, can be write like this:

{% highlight csharp %}
    public Item GenerateRandomItem(Transform dropper)
    {
        float r = Random.value;
        int itemLevel = (int)currentLevel;
        int enemyLevel = (int)dropper.gameObject.GetComponent<EnemyDropItemProc>().enemyLevel;
        if (r < 0.8)    // There is 80% to generate the same level item
        {
            itemLevel = enemyLevel;
        }
        else if (r < 0.9)    // 10% to generate 1 higher level item
        {
            itemLevel += 1;
        }
        else if (r < 0.95)   // 5% to generate 2 higher level item
        {
            itemLevel += 2;
        }
        else if (r < 0.96)   // 1% to generate particular, menas special, level item
        {
            itemLevel = (int)ItemLevel.Particular;
        }
        else
            return null;
// if the enemy itself is special level, it has more opportunity to drop special item
        if (enemyLevel == (int)ItemLevel.Particular)
        {
            if (Random.value < 0.33)
            {
                itemLevel = (int)ItemLevel.Particular;
            }
        }
        itemLevel = (itemLevel < allLevelItems.Length) ? itemLevel : (allLevelItems.Length - 1);

// call `GenerateRandomLevelItem` to finally drop a random item in this level
        Item droppedItem = allLevelItems[itemLevel].GenerateRandomLevelItem();
        Debug.Assert(droppedItem!=null);     
    
        droppedItem = (Item)GameObject.Instantiate(droppedItem, dropper.position, Quaternion.identity);
        droppedItem.SetupRandomPickableItem();

        return droppedItem;
    }
{% endhighlight %}

All droppable items would be managed in a script named `ItemsCollection`, it can return random , use function `GenerateRandomLevelItem`, or particular item from a particular item level list.

More details, please check the sample project [here]( https://github.com/hanhonglei/Shooter).


<script>
  (function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
  (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
  m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
  })(window,document,'script','https://www.google-analytics.com/analytics.js','ga');

  ga('create', 'UA-85986843-1', 'auto');
  ga('send', 'pageview');

</script>