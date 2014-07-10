---
layout: post
title: 我翻译的Full Circle的第一篇文章！（2）
categories:
- Diandian
tags:
- Linux, 
---
<p>但是，在XLib下编写游戏会导致灭亡。我们怎样做出像 Planet Penguin Racer 和Super Tux一样的游戏的呢？ </p>
<p>The main reason should be two inventions here: OpenGL and SDL. </p>
<p>这主要应该归结为两样发明：OpenGl和SDL。 </p>
<p>OpenGL opened a new world in computer graphics. Being mostly a Silicon Graphics thing, it was for sure a UNIX-friendly thing. </p>
<p>OpenGL打开了计算机图形处理的新世界。就像大部分硅芯片的图像处理一样，他是和Unix相兼容的。 </p>
<p>Of course, after passing the hurdles of getting a X window with OpenGL content. With OpenGL we could finally get our Quake after a hard workday. </p>
<p>当然，在经历了重重阻碍让X window成为OpenGL的一部分。用 OpenGL，经过努力，我们最终得到了Quake。 </p>
<p>And while OpenGL did great things for 3D graphics, It carried unnecessary weight to 2D Game Development. </p>
<p>当OpenGL在计算机3D图形方面做了很多贡献以后，它又肩负起2D开发这样一个不必要的使命。 </p>
<p> And the developer had two options: use the unaccelerated but closer to other 2D APIs XLib or to go with the (sometimes) accelerated but unnatural OpenGL; Some of them ran to GTK and other toolkits, but most got lost on this. And then came Sam Lantinga unify our battle cries. </p>
<p> 开发者有两个选择：第一，用未加速但是接近其他2D APIs XLib；第二，是接近加速但是违背OpenGL；他们一些人走向了GTK和其他一些开发工具，但是大部分人茫然了。后来，来了Sam Lantinga使我们重新到了一起。 </p>
<p>Sam Lantinga had to port a Macintosh emulator to Windows and Linux...But hey, coding a graphical system for every Operating System sounds a crazy thing. </p>
<p>Sam Lantinga 在（翻译问题had to port a Macintosh emulator to Windows and Linux...） 但是，呵，给每一个操作系统编写一个图形系统实在是一件令人疯狂的事。 </p>
<p>And it is. He had a simple but daunting idea: write an abstraction layer, called SDL, and the rest is history : He got Doom ported to SDL is 3 days! </p>
<p>他有一个简单但是令人畏缩的主意：编写一个提取层，叫做SDL，接下来的事情成为了历史。</p>
<p>Now we can use SDL in a huge variety of platforms, ranging from mobile devices (more about this below), Video Game Consoles , and lots of mainstream and obscure operating systems. </p>
<p>With SDL, developers could actually go through the &quot;create window for OpenGL&quot; novella in less than 10 lines of code.And binding for other languages spring every month or so. I bet he didn't see that coming.</p>
<p>现在，我们可以在多种平台上使用SDL。从移动设备、视频游戏控制器，到许多主流、非主流的操作系统。通过SDL，开发者们实际上可以用不到10行代码完成“为OpenGL创造视窗”。然后为其他语言封装？ 我打赌他没有看到这件事到来。 </p>
<p><strong>The Java Monster</strong> </p>
<p><strong>JAVA</strong><strong>怪物</strong></p>
<p>The hearts of millions of programmers (those include even John Carmack) were touched with this promise: &quot;Now we can write our own AAA game for all platforms&quot;.</p>
<p>成千上万的程序员的核心（他们甚至包括 John Carmack）接触这个承诺：“现在我们可以给所有的平台编写我们自己的AAA级的游戏”</p>
<p>Unfortunately, it took a while for the idea to catch on for real. What the Java applets really were able to do was a little below that.</p>
<p>不幸的是，让这件事成真花了一段时间。JAVA程序并没有做到之前所承诺的那样。 </p>
<p>But still, as Sun released their JDK for Linux, it was quickly possible to write Java applets on a Linux box and see them running on Macs and windows boxes. </p>
<p>但仍然，当Sun放出了Linux版本的JDk以后，它让在Linux编写Java程序再到Windows或者苹果机上运行编写的程序成为可能。</p>
<p>Basically , this was a time for small arcade clones and advergames.</p>
<p>这基本上是一个And for several startups funded for advergames, </p>
<p>the Linux + Java applets were the killer combo. Linux+ Java的程序模式是一个杀手组合. </p>
<p>Most of the technical staff of those came from those tech geeks who had been using Linux since college. </p>
<p>大部分技术人员来自到大学采用Linux的人群。</p>
<p>But still, the premier time for smooth Java game development was yet to come, and we will return to this later. </p>
<p>但是，优化Java游戏的最好时间当时还没有到来，并且我们现在将回到这之后。</p>
<p><strong>Take it in your Pocket</strong> </p>
<p><strong>把它放到你的口袋里面</strong></p>
<p>If mobile is the name of the game, you're lucky. Mobile development under UNIX have been strong since the beginning , with J2ME mostly, and now, more recently, with Linux Mobile. </p>
<p>如果手机是游戏的代名词，那么你很幸运。在Unix下的手机开发已经比开始的时候好多了，大部分通过J2ME，现在更多的是在Linux下。</p>
<p>With J2ME , there are plenty of possibilities. </p>
<p>有了J2ME，这里有很多中可能性。 </p>
<p>Some are more mature, like NetBeans and Sun WTK, and some brand new, like Nokia's WidSet. </p>
<p>一些是比较成熟的，像NetBeans 和 Sun WTK，还有一些是比较新的，像Nokia 的 WidSet。 </p>
<p>Linux is being taken seriously by the big players, as most innovations in terms of design comes from freedom fighters, like us.</p>
<p>Linux正在认真思考，通过那些大玩家 大多数就设计方面而言的革新是来自自由战士的，就像我们一样。The only possible downside of the approach might be the plethora of proprietary protocols mobile phones use to communicate with a computer through the data cables.唯一的坏处是过剩的连接电脑和手机的私有移动协议。 Be sure to purchase a phone that speaks &quot;Mass Storage Device&quot; to the computer.一定要为电脑购买“大容量存储设备”的手机。 </p>