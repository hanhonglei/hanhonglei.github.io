---
layout: post
title:  Add google analytics to the blog
date:   2016-10-20
categories: article
---
Cited from [here](http://romantsegelskyi.github.io/blog/2015/07/26/personal-page-blog/)

In case you love statistics or just curious if anyone visit you website, adding something to track visitor seems like a good idea. My choice was [Google Analytics](https://analytics.google.com) since it's relative simple and works great. To add analytics support go to Admin tab and create new account. After you enter all the needed information and accept the agreements, you will get tracking code, something like this:

{% highlight js %}
  (function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
  (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
  m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
  })(window,document,'script','//www.google-analytics.com/analytics.js','ga');

  ga('create', 'UA-65099615-1', 'auto');
  ga('send', 'pageview');
  
{% endhighlight %}

Insert this code anywhere at your `index.html` page and data will get automatically uploaded to analytics.

<script>
  (function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
  (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
  m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
  })(window,document,'script','https://www.google-analytics.com/analytics.js','ga');

  ga('create', 'UA-85986843-1', 'auto');
  ga('send', 'pageview');

</script>