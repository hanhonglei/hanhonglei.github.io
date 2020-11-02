---
layout: post
title:  "How to submit a game demo in the academic conference"
date:   2020-10-30
categories: article paper poster demo
---
# How to submit a game demo in the academic conference

目前，随着针对游戏的研究越来越深入，游戏相关的会议也越来越多。和其他学术会议类似，游戏相关的学术会议，可以投递研究论文，被接收之后，会被发表在会议论文集或者推荐到合作学术期刊发表。

会议一般还会接收更加多样化的成果报告，比如短文（short paper）、墙报（poster），这些类型的论文比普通论文要求稍低，如果对自己工作的贡献不是很有自信的话，可以投递这些类型的论文。

更为吸引人的是，这些会议往往还会接收偏创作类的工作成果，比如game demo。但和其他纯游戏设计比赛不同的是，提交的这些game demo要求有一定的探索性、创新型，比如探索某种新技术在游戏当中的应用，或者某种新的游戏设计理念、体验模式等。此外，还要求针对投递的游戏，写一篇短文，按照论文的要求来写，目的是论述game demo当中提出的创新性。要进行研究必要性、相关工作、本文方法、实验结果分析等方面的论述。相比于普通论文，在学术性方面要求不高，更关注工作的创新性和应用价值。这个game demo环节适合于专业型硕士甚至本科生，把自己的游戏专业创作撰写为论文投递。

下面四个会议是我整理的游戏相关的知名会议，除了最后一个会议仅接收普通学术论文之外，其他三个会议，都接收包括game demo在内的多种类型的研究成果。

1. [IEEE Conference on Games (CoG)](https://ieee-cog.org/2020) ，往年举办日期是8月份，截稿往年是3月底，[2021年安排](https://ieee-cog.org/2021/)还没有出来。接收论文类型很丰富，包括Short, competition, vision and demo papers. 
2. [Foundations of Digital Games](http://fdg2021.org/ ), 截稿日期: 25 January 2021，举办日期是8月份，接收论文中包括了game and demo类型（偏向于游戏设计和工程）
3. [CHI PLAY](https://chiplay.acm.org/2020/)，2021年的未出任何信息，往年举办日期是12月，截稿4月份,除了普通论文之外，包括Interactivity（类似于poster和demo）和Work in Progress（正在进行的工作）环节
4. [I3D：ACM SIGGRAPH Symposium on Interactive 3D Graphics and Games Online](http://i3dsymposium.github.io/2021/), 举办日期：20-22 April 2021，Paper submission deadline:December 22, 2020，包括普通paper和期刊paper两种（纯学术）。

接下来，以发表于2019年Foundations of Digital Games（上面第二个会议）上的一篇论文为例，来简单介绍一下这种类型论文的写作。该论文隶属于论文集中的“posters and demos”部分。

该论文题为[Rhythm dungeon: a blockchain-based music roguelike game](https://dl.acm.org/doi/10.1145/3337722.3341836),正如其名字所示，该论文介绍了一款基于区块链的音乐节奏地牢游戏。游戏中，需要玩家通过输入特定顺序的音乐节奏来探索roguelike地牢。该游戏的主要创新点是引入了区块链技术，这样通过智能合约，游戏中的敌人是其他游戏中生成的，共享同样的区块链。此外，玩家还可以在游戏结束的时候上传他们的角色，这些角色可以在其他游戏中出现并产生影响。该游戏的设计和实践是要说明，利用区块链技术提供的大量玩家间的异步交互，在游戏中得到去中心化的游戏体验的可能性。

在文章的第一部分INTRODUCTION中，作者分析了当前市面上比较流行的区块链技术的游戏，指出他们的问题是新的游戏可以复用旧的游戏的token，但新游戏中对token的修改不会影响到旧的游戏，这种影响是单向的。而文章展示的这款游戏，则可以和另外两款已经发布的区块链游戏，实现互操作interoperability。

文章的第二部分是SYSTEM FRAMEWORK系统架构，介绍了作者开发的这款游戏，如何实现和另外两款已经发布的游戏（也是作者使用同样的平台开发的）实现资产的重用，并且实现了互操作。也就是作者开发的新游戏中的角色可以可以和旧游戏中的角色交互，新游戏中新创建的角色，还可以出现在旧游戏当中。

第三部分GAMEPLAY介绍了游戏的玩法。

第四部分GAME FEATURES主要分析了作者开发的这款游戏的特色。其中之一是如何实现玩家之间的异步交互，另外一个是上传个性化角色。

第五部分ONGOINGWORK分析了本游戏可能存在的改进空间。

最后一部分CONCLUSIONS做了简单总结。

希望有志于从事游戏设计的你，也能够在自己的创作过程中，多一些思考和探索。将一些新技术、新设计理念，制作为游戏demo的形式，通过玩家调研等方式来验证这些技术、理念的效果，在有了一定数据的基础上，将其撰写为论文，并投递到这些会议的对应单元中。

有想法的话，欢迎和我联系 hanhonglei@cuc.edu.cn


<script>
  (function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
  (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
  m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
  })(window,document,'script','https://www.google-analytics.com/analytics.js','ga');

  ga('create', 'UA-85986843-1', 'auto');
  ga('send', 'pageview');

</script>