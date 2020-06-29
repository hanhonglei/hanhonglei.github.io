---
layout: post
title: Be aware of execute order in Unity
date: 2016-11-9
categories: article unity programming
---
<!--more-->

## Be careful of the efficient time of game object when active

Game object may not be really active when using function `SetActive(true)`. It’s better to run any related function of this game object after the next frame.

{% highlight csharp %}

    void Update()
    {
        if (!answerUI.activeSelf)
        {
            if (currentTime > levelTime || Input.GetKeyDown(KeyCode.Space))	// when user study scene is done, or user presses space bar
            {
                answerUI.SetActive(true);
            }
        }
        else if (allObjects.activeSelf)
        {
		// ! safe to call the answerUI function in the next frame
            answerUI.GetComponent<UserInputs>().BeginAnswer();

            allObjects.SetActive(false);
        }
        }
    }
{% endhighlight %}

## Execution Order of Event Functions

### First Scene Load

These functions get called when a scene starts (once for each object in the scene).

- `Awake` This function is always called before any Start functions and also just after a prefab is instantiated. (If a GameObject is inactive during start up Awake is not called until it is made active.)
- `OnEnable` (only called if the Object is active): This function is called just after the object is enabled. This happens when a MonoBehaviour instance is created, such as when a level is loaded or a GameObject with the script component is instantiated.
- `OnLevelWasLoaded` This function is executed to inform the game that a new level has been loaded.

Note that for objects added to the scene, the `Awake` and `OnEnable` functions for all scripts will be called before `Start`, `Update`, etc are called for any of them. Naturally, this cannot be enforced when an object is instantiated during gameplay.

### Before the first frame update

`Start` Start is called before the first frame update only if the script instance is enabled.

For objects added to the scene, the Start function will be called on all scripts before `Update`, etc are called for any of them. Naturally, this cannot be enforced when an object is instantiated during gameplay.

### In between frames

`OnApplicationPause` This is called at the end of the frame where the pause is detected, effectively between the normal frame updates. One extra frame will be issued after OnApplicationPause is called to allow the game to show graphics that indicate the paused state.

### Update Order

When you’re keeping track of game logic and interactions, animations, camera positions, etc., there are a few different events you can use. The common pattern is to perform most tasks inside the `Update` function, but there are also other functions you can use.

- `FixedUpdate` FixedUpdate is often called more frequently than `Update`. It can be called multiple times per frame, if the frame rate is low and it may not be called between frames at all if the frame rate is high. All physics calculations and updates occur immediately after `FixedUpdate`. When applying movement calculations inside `FixedUpdate`, you do not need to multiply your values by `Time.deltaTime`. This is because `FixedUpdate` is called on a reliable timer, independent of the frame rate.
- `Update` Update is called once per frame. It is the main workhorse function for frame updates.
- `LateUpdate` LateUpdate is called once per frame, after `Update` has finished. Any calculations that are performed in `Update` will have completed when LateUpdate begins. A common use for `LateUpdate` would be a following third-person camera. If you make your character move and turn inside `Update`, you can perform all camera movement and rotation calculations in `LateUpdate`. This will ensure that the character has moved completely before the camera tracks its position.

### When the Object is Destroyed

`OnDestroy` This function is called after all frame updates for the last frame of the object’s existence (the object might be destroyed in response to `Object.Destroy` or at the closure of a scene).

### When Quitting

These functions get called on all the active objects in your scene:

- `OnApplicationQuit` This function is called on all game objects before the application is quit. In the editor it is called when the user stops playmode.
- `OnDisable` This function is called when the behaviour becomes disabled or inactive.

<script>
  (function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
  (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
  m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
  })(window,document,'script','https://www.google-analytics.com/analytics.js','ga');

  ga('create', 'UA-85986843-1', 'auto');
  ga('send', 'pageview');

</script>