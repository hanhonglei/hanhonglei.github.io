---
layout: page
title: Projects 项目
permalink: /projects/
image: /Images/prepage.jpg
---
## 1.	[Yotta](https://github.com/hanhonglei/Yotta)
![]({{site.url}}/Images/Proj/yotta.jpg){:width="300px"}

2D tower defense game based on Unity.

YOTTA（游塔）是一款以景区旅游为主题的类塔防游戏。

游戏将塔防和模拟经营这两种游戏类型元素相结合，玩家既能够从游戏中体验到模拟经营元素中建筑摆放美感与功能资源搭配的趣味，同时也要尽力在关卡内所有游客走出景区前达成胜利通关的条件。

所获奖项:

- 2014年“Fancy3D原创游戏大赛”校园组 最佳表现奖，北京青果灵动科技有限公司与创意云平台，北京2014年
- 2015年“中国动漫游戏创投奖”游戏类 创投提名奖，中国动画学会，深圳2015年

制作人员：

- 制作人：韩红雷
- 指导老师：费广正、成星
- 策划：黄邦宁、吴婉乔
- 程序：徐婵婵
- 美术：李萌、邹悦、张思雨
- 单位：中国传媒大学艺术学部

## 2.	[Shooter](https://github.com/hanhonglei/Shooter) 
![]({{site.url}}/Images/Proj/shooter.jpg){:width="300px"}

This is a demo Unity 3D project for education purpose. It has many typical game features as list below:

- 3rd Person controller
- Using Mecanim
- Enemy patrol, and react
- Weapon system
- Adding interactive items
- Dropping random items
- UI

## 3.	[A demo using Leapmotion in VR environment](https://bitbucket.org/Honglei_Han/leapmotioncontrolvrdemo)
![]({{site.url}}/Images/Proj/lm.jpg){:width="300px"}

A tower defense game in VR environment using Leapmotion as the interactive method.

There are two methods to play this game. One is traditional method, using keyboard and mouse. The other one is using VR glasses and leap motion hand controller.

## 4.	[Lottery](https://github.com/hanhonglei/Lottery) 
![]({{site.url}}/Images/Proj/lottery.jpg){:width="300px"}

Use Microsoft MFC, and use skin to beautify. Can generate the lucky numbers randomly.

## 5.	[MyPHDProject](https://github.com/hanhonglei/PHDProject)
![]({{site.url}}/Images/Proj/doctor.jpg){:width="300px"}

Used in Honglei Han's PHD study and graducation. Please check the readme.doc for more details.

## 6. [Samples of my book Game Development Programming Foundation](https://github.com/hanhonglei/GameDevelopmentSamples)
![]({{site.url}}/Images/Proj/cBook.jpg){:width="300px"}

Samples of all chapters in the book `Game Development Programming Foundation`

They are all programmed using `C/C++` language, and built successfully in `Microsoft Visual Studio 2010` using `Win32` framwork.

In some PC that never installed `Visual Studio`, may require Microsoft Visual C++ 2010 Redistributable Package which can be downloaded from [here](http://www.microsoft.com/en-us/download/details.aspx?id=5555).

Usage:

You can open all samples in the `Visual Studio` project named `GameDevelopmentHan`, or you can open them separately from their own folders using `Visual Studio`.

More information please check from the book [here](http://product.dangdang.com/23951820.html), or [here](http://www.cuc.edu.cn/cgzt/5564.html).

## 7. [User Study of the Paper Implicit measures of user attention in virtual environment navigation](https://github.com/hanhonglei/UserAttentionUserStudy)
![]({{site.url}}/Images/Proj/Gaze.jpg){:width="300px"}

User Study of the Paper [Implicit measures of user attention in virtual environment navigation](https://hanhonglei.github.io/publications/)

`Abstract`: The eye-tracker device is the main tool to obtain visual attention. However, it is hard to be applied in the 3D virtual scene navigatipron because of its poor reliability, great complexity and high price. We propose a new attention measure metric which can be easily embedded in the virtual environment. Behaviors of virtual camera controlled by the user are regarded as implicit expression of visual attention. The implicit expression is parameterized by the observed object’s distance to the center of the camera, occlusion, projected area, and observation time. A sophisticated user study experiment is designed to verify the reliability of this kind of measurement. The proposed implicit measurement of user attention can be effectively applied to an application of user attention aided game design.

This is the user study `Unity 3D` application of [this paper](http://info.scichina.com:8084/sciF/CN/Y2014/V44/I11/1398).

During user navigating, all attention evaluation parameters, proposed in this paper, of different saliency game object will be recorded in different files located in folder `Output`. The player navigate behavior will be recorded as well.

After collect enough samples, a user attention measure result of different saliency level game object will be obtained. The attention value can be calculated based on these parameters using the method proposed in the [paper](http://info.scichina.com:8084/sciF/CN/Y2014/V44/I11/1398).

## 8. [Linear Texture Coordinate Interpolation in Rasterization](https://github.com/hanhonglei/Linear-Texture-Coordinate-Interpolation-in-Rasterization)
![]({{site.url}}/Images/Proj/lena.jpg){:width="300px"}

This is the source project of paper [Linear Texture Coordinate Interpolation in Rasterization](http://www.jcad.cn/jcadcms/document/attach_manager!download.action?id=4028e4e44bc55348014c2be463d81403) in Chinese.

You can also find the information of this paper in the `publications` page [here](https://hanhonglei.github.io/publications/)

**Abstract** A new algorithm is presented for correct texture coordinate interpolation in rasterization. By dividing the 3D ploygon into line segments parallel to the viewing plane, the algorithm performs texture coordinate interpolations along these line segments, so that correct results can be obtained with linear computation, without the division operations as used in existing methods for rasterization. For the errors from discretization in rasterization, supplementary measures are provided to correct them gradually. Experiment results show the effectiveness and efficiency of the new algorithm. 

**Howt to use**

- 使用`打开文件`打开一张`tga`格式的纹理（比如`棋盘.tga`），也可以直接将`tga`图片拖拽上去。
- 点击`R`按钮可以再`OpenGL`绘制和自主栅格化之间切换。
- 点击`C`可以调整三角形的几何信息；以及采取哪种栅格化方式（两种：文章提出的`KIM`，以及我们提出的`WANG`）。
- 使用方向键以及换页键可以调整视角。
- 每种栅格化方式的时间在窗口中给出，单位毫秒。
- 如果`Raster.exe`运行不正确，请首先安装`vcredist_x86.exe` [here](https://www.microsoft.com/en-us/download/details.aspx?id=5555)。
- 大部分算法在`Raster.cpp`中，并有注释。
- 增加了调整纹理坐标精度的选项，可以调整保留到纹理坐标小数点后几位。
- 程序退出后，会在当前文件夹下生成`OutPut.txt`文件，里面保存了各种栅格化算法的统计数据。

## 9. [OpenGL MFC Framework](https://github.com/hanhonglei/OpenGLMFCFramework)
![]({{site.url}}/Images/Proj/opengl.jpg){:width="300px"}

A `MFC` framework for `OpenGL` applications. It can be used as a startup project for `OpenGL` applications based on `MFC`.

The features are listed below.

- How to configure environment parameters for `OpenGL` application, and the release stuff when application exits.
- Some fallible issues when developing `OpenGL` application based on `MFC`, such as twinkle effect when the window changes.
- Some issues should be considered when implementing `scroll view’
- How to open a `TGA` file into an `OpenGL `application.

## 10. [2D character animation based on standing foot to avoid sliping](https://github.com/hanhonglei/2DCharacterAnimMaker)
![]({{site.url}}/Images/Proj/anim.jpg){:width="300px"}

This is the source project of paper [基于分层图像的建模与漫游]({{site.url}}/Resources/2007LayerImage.pdf) in Chinese.

You can also find the information of this paper in the `publications` page [here](https://hanhonglei.github.io/publications/)

- More information, please feel free to visit my personal website [here](https://hanhonglei.github.io/).

**本程序实现的功能是** 利用用户交互来得到比较真实的动画。

**本程序所使用的技术有** spline曲线拟合等。

本软件使用了Win32控制台程序结构，使用命令行来传递程序参数。

需要首先设定2个程序运行参数：第一是所要调入`Gif`图像的文件名（如果不再当前文件夹下，需要指定详细路径）；第二是所调入角色运动的朝向（`r`表示向右，`l`表示向左）。
比如，用户需要处理名为brachio的gif角色动画，则需要在`bat`文件中输入必要参数如下：

{% highlight csharp %}
AnmTest.exe brachio.gif r
{% endhighlight %}

<script>
  (function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
  (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
  m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
  })(window,document,'script','https://www.google-analytics.com/analytics.js','ga');

  ga('create', 'UA-85986843-1', 'auto');
  ga('send', 'pageview');

</script>
