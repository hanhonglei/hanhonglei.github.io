---
layout: post
title: Some frequent used synax of Jekyll
date: 2016-10-29
categories: article Jekyll
---
<!--more-->

1. Use `   ` pair to get special format of the content inside them.
2. Use double stars `**` pair to get bold formatted content.
3. Use {% raw %} `{% highlight csharp %} {% endhighlight %}` {% endraw %} to format code. There are quite a few types of language are supported.
4. Use `{``%` `raw` `%``}` `{``%` `endraw` `%``}` to only display common text content instead of execute the code inside them.
5. Use `-` to get a comment pattern.
6. Different number of `#` represents different level of title.
7. Treat user defined `<!--more-->` as the beginning of main content of the article. Before it is the abstract.
8. Use {% raw %} `![Myself]({{site.url}}/Images/Me.jpg "Optional title"){:height="150px"}` {% endraw %} to insert and resize an image. `site.url` means the base website address that can be defined in `_config.yml` like this: `url: "https://hanhonglei.github.io"`.
9. Use`[]` pair to indicate a hyperlink, follow up a `()` pair with a website address inside it. Such as {% raw %} `[Shooter](https://github.com/hanhonglei/Shooter)` {% endraw %}
10. You can produce a horizontal rule tag by placing three or more hyphens, asterisks, or underscores on a line by themselves. `***` or `____`


<script>
  (function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
  (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
  m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
  })(window,document,'script','https://www.google-analytics.com/analytics.js','ga');

  ga('create', 'UA-85986843-1', 'auto');
  ga('send', 'pageview');

</script>