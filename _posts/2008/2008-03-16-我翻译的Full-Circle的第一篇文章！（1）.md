---
layout: post
title: 我翻译的Full Circle的第一篇文章！（1）
categories:
- Diandian
tags:
- Linux, 
---
翻译：贾庆祥（Lee）(回来了，对不起，最近比较忙，连夜翻译现在) &amp; sctronlinux &nbsp;&nbsp;
<br />翻译状态：100%
<br />校对：
<br />校对状态：
<br />二校：
<br />二校状态：
<br />繁体：
<br />繁体状态：备注（贾庆祥说）：连夜翻译加上早晨的翻译，终于翻完了，在这里，对没有按时完成向大家道歉。 IndependentGameDevelopment 独立游戏开发
<p> </p>
<br />
<p>(redirected from <a href="http://fullcirclemagazine.org/docs/pmwiki.php?n=Issue10.IndependentGameDevelopment?action=edit">Issue10.IndependentGameDevelopment</a>) </p>
<p>This is longer than the word count but thats ok as this is a good, interesting, article. </p>
<p> </p>
<p>In the past years, independent (indie) game development went from sitting on dark basement, staring a black and white screen, fiddling cryptic messages to decode the VGA registers in order to achieve the maximum performance to sitting on a dark basement while staring to gorgeous GNOME or KDE screen while tossing the maximum performance from your GPU with no sweat. (Of course , some of us still love that darn pretty black screen)</p>
<p> </p>
<p>近些年来，独立游戏开发越来越陷入一个误区，从为了达到最棒的效果而使用VGA（视频图形接口）中的隐秘方法来点缀黑白屏幕，到为了产生华丽的GNOME或者KDE界面，突破最大的GPU性能，从而榨干GPU（图形处理器）。（当然，我们某些人仍喜欢用其去装饰那漂亮的黑色屏幕）。</p>
<p> </p>
<p>From these dark ages to current days, Linux game development went from an adventure to some serious play, as the tools matured and CG companies took Linux more seriously as a development platform.</p>
<p> </p>
<p>从很久以前到现在，Linux游戏开发一开始是次大胆的冒险，并逐渐成为成熟的工具，越来越多的CG公司将Linux作为开发平台。</p>
<p> </p>
<p>This article intends to present the reader with some good options on Linux game development, while analyzing the reasons of this Linux game development takeoff.</p>
<p> </p>
<p>这篇文章想呈现给读者一些很好的在Linux游戏开发，而分析Linux游戏开发的腾飞。</p>
<p> </p>
<p><strong>The Dark Ages</strong> </p>
<p>黑暗的年代 </p>
<p>Picture this: You have a pretty console screen on your machine. What are your gaming options? None, you might answer. You couldn't be more wrong. </p>
<p>Before XServers were commonplace, there were already a struggling game development community. </p>
<p>想象这个： 你的电脑配了一个非常好的屏幕。你的游戏选项是什么呢？不，你可能会回答，你不能再错了。在Xserver 被人们习惯以前，这里已经有了一个努力奋斗的社区。 </p>
<p>Most of them came from the existent BSD community and saw a good potential with that &quot;fast and lightweight UNIX&quot; that Linux was (today, both Linux and BSD seen to be in the same level) and then we got our share of console games, like dopewars and other console classics. </p>
<p>社区的成员大部分来自与与存在的BSD社区并且他们看到了Linux的“更快更轻量级的UNIX”的潜力（现在，Linux和BSD都差不多）然后我们开始共享我们的游戏控制平台，像dopewars 和其他一些经典平台。 </p>
<p>Needless to say, developing this games was more challenging than playing them, as they didn't have the tools available today. But these dark ages wouldn't last long. </p>
<p>不用说，开发游戏比起玩游戏要难得多。而且当年他们没有现在这么好的编程条件。好在“黑暗的日子”没有持续太长。 </p>
<p><strong>The Golden Age of Unix Graphics Evolution</strong> </p>
<p>Unix图形处理演变的黄金时代 </p>
<p>Since the start of the modern computing industry, UNIX was the de facto standard for serious applications and before the Mac take-over, UNIX was the absolute king for computer graphics. </p>
<p>自从现代计算机工业的开始，Unix是严格的应用程序的实际上存在的标准在苹果机出现以前。Unix计算机图形领域的绝对领袖。 </p>
<p>Then it came. The graphical revolution for the UNIX workstation. First, it was a industry or office thing only, but then, we gradually , got a XServer running on our machines. </p>
<p>时间在流逝。Unix工作站的图形革命开始了。最初，它只是工业上的产物，但是，一段时间以后，逐渐演变为运行在我们电脑上的Xserver。 </p>
<p>But still, coding a game in XLib can lead to suicide. How did we get such great games like Planet Penguin Racer and Super Tux? </p>
<p>Quake一样的经典游戏？现在，开始吧！</p>