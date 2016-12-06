---
layout: post
title: How to make a 3rd person controller shoot game using Unity 3D (4-6)
date: 2016-12-5
categories: article unity game shooter tutorial
---
<!--more-->

## 4 Actor AI

- Find source project Tutorial_3_AI_2 in [Shooter](https://github.com/hanhonglei/Shooter) 

### The logic

The enemy patrols in a particular path. When he sees the player, he would try to chase him. If he can't catch with the player, he would go back to patrol.

### The sight of enemy

Create an empty game object named `EnemySight`. Add a sphere collider to it, adjust the radius, and set it as `Trigger`.

![]({{site.url}}/Images/shooter/image19.png){:height="300px"}

Set the sight game object as the child of the enemy. Give it a script named `EnemySight`. The script can judge whether the player is inside the sight of the enemy or not. In `Enemy` script, it will be used as the option if the enemy chase the player or patrol.

{% highlight csharp %}
// This is a collider trigger as the child of the enemy
public class EnemySight : MonoBehaviour
{
    public float fieldOfViewAngle = 110f;           // Number of degrees, centred on forward, for the enemy see.
    public bool playerInSight;                      // Whether or not the player is currently sighted.
    public Vector3 personalLastSighting;            // Last place this enemy spotted the player.
    public static Vector3 resetPos = Vector3.back;
    private GameObject player;                      // Reference to the player.

    void Awake()
    {
        player = GameObject.FindGameObjectWithTag("Player"/*Tags.player*/);

        // Set the personal sighting and the previous sighting to the reset position.
        personalLastSighting = resetPos;
    }

    void OnTriggerStay(Collider other)
    {
        // If the player has entered the trigger sphere...
        if (other.gameObject == player)
        {
            // By default the player is not in sight.
            playerInSight = false;

            // Create a vector from the enemy to the player and store the angle between it and forward.
            Vector3 direction = other.transform.position - transform.position;
            float angle = Vector3.Angle(direction, transform.forward);

            // If the angle between forward and where the player is, is less than half the angle of view...
            if (angle < fieldOfViewAngle * 0.5f)
            {
                RaycastHit hit;

                // ... and if a raycast towards the player hits something...
                if (Physics.Raycast(transform.position + transform.up, direction.normalized, out hit, col.radius))
                {
                    // ... and if the raycast hits the player...
                    if (hit.collider.gameObject == player)
                    {
                        // ... the player is in sight.
                        playerInSight = true;

                        // Set the last global sighting is the players current position.
                        //lastPlayerSighting.position = player.transform.position;

                        personalLastSighting = player.transform.position;

                    }
                }
            }
        }
    }

    void OnTriggerExit(Collider other)
    {
        // If the player leaves the trigger zone...
        if (other.gameObject == player)
            // ... the player is not in sight.
            playerInSight = false;
    }
}
{% endhighlight %}

### Patrol

In enemy behavior script, `EnemyPatrol`, use enemysight to control the enemy patrol status. Set stopping distance in `NavMeshAgent` component inspection to a acceptable value.

![]({{site.url}}/Images/shooter/image20.png){:height="300px"}

The statuses of the enemy can be switched between patrol, chase, and other behaviors. Use sight, distance to the player, and other parameters to determine the status.

Next turoial please click [Weapon and other advanced game functions]({{site.url}}/article/unity/game/shooter/tutorial/2016/12/05/unity-shooter-tutorial-5.html).

More details, please visit the project [here](https://github.com/hanhonglei/Shooter) 


<script>
  (function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
  (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
  m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
  })(window,document,'script','https://www.google-analytics.com/analytics.js','ga');

  ga('create', 'UA-85986843-1', 'auto');
  ga('send', 'pageview');

</script>