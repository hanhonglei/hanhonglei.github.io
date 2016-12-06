---
layout: post
title: How to make a 3rd person controller shoot game using Unity 3D (2-6)
date: 2016-12-5
categories: article unity game shooter tutorial
---
<!--more-->

## 2 Mecanim

- Find source project Tutorial_2_Animation in [Shooter](https://github.com/hanhonglei/Shooter) 

![Create a new scene]({{site.url}}/Images/shooter/image1.png){:height="300px"}

- Animation clips are imported from an external source or created within `Unity`.
- The animation clips are placed and arranged in an `Animator Controller`.
- The rigged character model has a specific configuration of bones which are mapped to Unity’s common `Avatar` format.
- When animating the character model, it has an `Animator` component attached

![Mecanim]({{site.url}}/Images/shooter/image9.png){:height="300px"}

Animation Transitions

![]({{site.url}}/Images/shooter/image10.png){:height="300px"}

Use parameters to control state transit. The parameter can be retrieved through script.

![]({{site.url}}/Images/shooter/image11.png){:height="300px"}

Using multi-layer animation.

![]({{site.url}}/Images/shooter/image12.png){:height="300px"}

### Mask

The Mask property to specify the mask used on this layer.

For example if you wanted to play a throwing animation on just the upper body of your model, while having your character also able to walk, run or stand still at the same time, you would use a mask on the layer which plays the throwing animation where the upper body sections are defined.

![]({{site.url}}/Images/shooter/image13.png){:height="300px"}

### Set the mask to the new layer

Use mask in a additive layer that exclude legs.

When transit to a animation clip in this layer, it would only replace the animation of upper body.

![]({{site.url}}/Images/shooter/image14.png){:height="300px"}

Next turoial please click [Actor AI]({{site.url}}/article/unity/game/shooter/tutorial/2016/12/05/unity-shooter-tutorial-3.html).

More details, please visit the project [here](https://github.com/hanhonglei/Shooter) 


<script>
  (function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
  (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
  m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
  })(window,document,'script','https://www.google-analytics.com/analytics.js','ga');

  ga('create', 'UA-85986843-1', 'auto');
  ga('send', 'pageview');

</script>