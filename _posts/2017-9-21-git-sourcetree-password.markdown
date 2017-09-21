---
layout: post
title:  "Lost ablity to authenticate in SourceTree"
date:   2017-9-21
categories: article sourcetree github
---
## Question
After auto-upgrade of SourceTree, the UI tool lost the ability to authenticate using SSH keys when I need to Push. However, if I go to the Terminal window, it asks me for password, and completes the PUSH command.

## How to solve
I finally got it to authenticate by updating the embedded git (didn't fit it alone) and deleting AppData\Local\Atlassian\SourceTree\passwd. Restarted SourceTree and it prompted for my password. Pushes then started working again.

- Frome [here](https://jira.atlassian.com/browse/SRCTREEWIN-7727?_ga=2.182584230.1425524081.1505987187-1519565448.1488987063)


<script>
  (function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
  (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
  m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
  })(window,document,'script','https://www.google-analytics.com/analytics.js','ga');

  ga('create', 'UA-85986843-1', 'auto');
  ga('send', 'pageview');

</script>