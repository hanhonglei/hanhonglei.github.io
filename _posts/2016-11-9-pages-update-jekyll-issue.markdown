---
layout: post
title: Some issues after updating Jekyll resources
date: 2016-11-9
categories: article Jekyll pages update
---
<!--more-->

After updating the GitHub pages Jekyll resources useing `bundle update`, there are quite a few problems. Based on internet resolutions. Below are some tricks should be considered.

1. Download and install `Python 2.7` from [here](https://www.python.org/downloads/), not the latest version but only version 2.7
2. Recall `minima` gem. You have to first locate your minima gem:

	```
	bundle show minima
	```

	Will give you something like `/very/long/path/to/2.2.0/gems/minima-1.0.1`. You can then copy/paste `_includes`, `_layouts` and `_sass` folders from your gem to your site root from the file explorer.
	Or you can do it with the command line from your root:

	```
	cd your/root/folder
	cp -R `echo "$(bundle show minima)/_*/"` .
	```

	Your site will now work on `gh` pages. And theme gem is now useless, because overridden by copied files. Please check the answer [here](http://stackoverflow.com/questions/38772179/jekyll-work-in-local-but-not-work-github-file-to-import-not-found-or-unreadable).


<script>
  (function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
  (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
  m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
  })(window,document,'script','https://www.google-analytics.com/analytics.js','ga');

  ga('create', 'UA-85986843-1', 'auto');
  ga('send', 'pageview');

</script>