---
layout: post
title: 我翻译的Full Circle的第一篇文章！（3）
categories:
- Diandian
tags:
- Linux

---
<p>Recently , we have seen some companies going with Linux for their mobile OS'es. </p>
<p>最近，我们看到一些公司为了他们的手机操作系统开始和Linux走到一起了， </p>
<p>We all gain with that: this mobile Linux is not that different from our desktop machine and most SDKs use technologies broadly available. </p>
<p>我们都认为：这个移动Linux和一般的我们使用的桌面Linux没有什么区别，并且大部分SDK都是兼容的。Its like playing with your childhood friend's child.这个有点像和你的童年朋友玩耍。 </p>
<p>One Common point when dealing with mobile game development is the use of Simple DirectMedia Layer.</p>
<p>进行移动设备的程序开发的共同点是用简单的直接媒介层。 </p>
<p>Most mobile distros allow SDL apps to run with privileged speeds. </p>
<p>大部分移动发行版允许SDL高速运行。</p>
<p>The biggest distros here are: QTopia, from Trolltech (the guys that gave us libqt), EZX (QTopia based), from Motorola (some warnings apply here, as it doesnt run native applications right out-of-the-box), and mostly Maemo (the one your humble writer is most likely to code in day-to-day), from Nokia and finally OpenMoko, that is a joint effort to produce a distro for mobile phones. </p>
<p>最大的发行版是：QTopia，出自Trolltech（就是给我们libqt的那些人）；EZX（QTopia的基础），出自摩托罗拉(一些警告适用于此：它不能运行设备以外的本地程序)；还有Maemo（我天天为这个编写程序），来自诺基亚和OpenMoko，他们共同努力为移动电话编写发行版。<br />Also worth mentioning that Ubuntu Mobile is to become a great mobile OS, incorporating the UI from Maemo. Looks very promising. </p>
<p>另外也值得一提的是Ubuntu 移动，经要变成一个强大的移动操作系统，包含来自Maemo的界面，看起来很有有前途。</p>
<p><strong>The Dawn of the Desktop</strong> </p>
<p><strong>桌面应用的黎明</strong></p>
<p>As Linux evolved from the last decade, we could stop worrying about or desktop and could concentrate on producing something. </p>
<p>当Linux发展的最近十年，我们可以停止关于桌面能否集中精力与开发。 </p>
<p>This is a byproduct of projects like Ubuntu, that aims to bring more focus to the developers, putting them to do their best were they excel. </p>
<p>Ubuntu就是其中一个项目的副产品，项目原本是集中精力让开发人员做他们擅长的事情的。</p>
<p>There are also smaller efforts on some countries, like Brazil, to use Linux as a medium of knowledge broadcast, creating social projects that called for more average-joe-friendly desktops. 这对一些国家也有一些小的效果，比如巴西，通过把Linux作为一个只是的传播媒介，建立了了社会性的要求更多的average-joe-friendly desktops。Those are fertile field for Linux gaming.这都是Linux游戏多产的地区。 </p>
<p>Also, there are other companies using Linux for notebooks (but this distinguish from mobile Linux, as there is a full Linux machine experience), like ASUSTEK with its EeePC and OLPC (the last one making big bets on educational gaming), each being too big to cover here. </p>
<p>这里也还有一些其他公司用Linux技术为笔记本开发产品。（但这个要和手机上的Linux区分开来，这是一个完整的Linux机器体验）像话说的EeePC和OLPC（最后的版本在教育游戏上下了很大的赌注），他们俩都太大而没法在这讨论。</p>
<p><strong>Name Your Monster</strong> </p>
<p><strong>命名你自己的“怪兽”</strong></p>
<p>Now that you cant wait more to get your hands dirty, I will show you some good options for developing your own games. </p>
<p>现在，你不能等待了，我将向你提出一些开发你自己的手机游戏的好选择。</p>
<p><strong>Desktop</strong> </p>
<p>emacs (or your favorite text editor) + g++ : Thats right! chances are that the exact machine your are using to read this text is capable of game development. </p>
<p>emacs （或者你自己喜欢的文字编辑器）+ g++：那没错！问题在于你正在用于开发游戏的电脑可以阅读这些代码。 </p>
<p>Although the experience can be somewhat spartan, its perfectly possible. 虽然经历有点点斯巴达 但是那是完全有可能的。 </p>
<p>Except for a few moments I ran for some better tools, I went this way to develop my own 3D mobile game engine (www.sf.net/projects/bzk). </p>
<p>除了有时候我会用一些更好的工具，其他时候我都用这种方式开发我的3D手机游戏引擎。 </p>
<p><strong>Mobile</strong> </p>
<p><strong>移动设备</strong></p>
<p>If you're going for Java, make sure you take NetBeans, as it have a very strong mobile support.</p>
<p>如果你想用Java开发，确定你用NetBeans，因为它对在手机上的开发有很强大的支持。Don't forget your &quot;mobility pack&quot; for the chosen mobile device profile.不要忘记你为不同移动设备准备的“随意包”。 </p>
<p>If not, you're gearing towards Linux mobile which is good and bad news:<br />如果不是这样，你可以转到Linux移动平台，这里有一条好消息和一条坏消息： </p>
<p>The good: most of your existent desktop code will work out of the box. </p>
<p>好消息：大部分为Linux桌面应用编写的代码都可以在移动设备里使用。 </p>
<p>The bad: you will, probably (as most mobile devices use ARM processors which are incompatible with our x86 machines) need to recompile it with some esoteric SDK. And this will depend on the target platform. Some are easy, some are not. Make sure to also research what the best settings for your workstation are - sometimes, virtualization can be a viable option. </p>
<p>坏消息：你或许将（因为大部分的移动设备使用ARM处理器，而这个ARM处理器和我们常用的X86电脑的处理器是不兼容的）要用一些机密的SDK重新编辑 它们。这个取决于你要为哪个移动平台编写程序。有些简单，有些则不然。也要研究一下对于你的工作站的最佳设置是什么：有时候，虚拟机是一个很好的选择。 </p>
<p>One piece of good advice might be to use SDL. I can attest this, as I do most of my development on my desktop environment and when I feel the need, I just switch to the mobile SDK (in my case, Maemo SDK under Scratchbox), recompile, generate a Debian ARM package and test it on device (Nokia N770). This can save you valuable debugging time. </p>