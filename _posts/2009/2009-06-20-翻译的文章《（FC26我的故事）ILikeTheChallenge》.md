---
layout: post
title: 翻译的文章《（FC26我的故事）ILikeTheChallenge》
categories:
- Diandian
tags:
- Linux

---
<p>ILikeTheChallenge</p>
<p>A few months ago, I bought a laptop without an operating system. I installed Ubuntu 8.04 (Hardy Heron), which I received from shipit.ubuntu.com a few weeks earlier.</p>
<p>我喜欢挑战</p>
<p>几个月前，我买了一个没附带操作系统的笔记本电脑。我安装了几周前从shipit.ubuntu.com申请获得的Ubuntu 8.04 （Hardy Heron）。</p>
<p>This was the first time I had used Linux. When my friend took a look at my hard drive, he suggested that I make an additional partition to separate the operating system and data. He said this will be useful when I want to reinstall the operating system, or if there is something wrong with the system. I tried to create a partition (apart from the root partition (/) and swap area) while reinstalling Ubuntu. After creating partitions, I saw the partition contained a “lost+found” folder only, and I was confused why I couldn't create folders and copy data to the partition.</p>
<p>这是我第一次使用Linux。当我的朋友看了看我的硬盘时，他建议我划一个额外的分区来把操作系统数据和文件数据分开来。他说这样会使得我想重装系统或者系统有问题的时候比较方便。我努力创建了一个分区（区别于根分区（/）和交换分区）在我安装Ubuntu的时候。在创建了新分区以后，我看见分区只是包含了一个叫做“lost+found”的文件夹。我很疑惑为什么我不能在这个分区创建文件夹、拷贝数据。</p>
<p>So I reinstalled Ubuntu again to make sure I did a proper installation, but I still couldn't access the additional partition. Then I asked another friend, who also uses Ubuntu, for help. He told me to mount the partition for the operating system as root (/), then create a partition for the swap area (the size is twice the memory size), and mount the other partition as /home.</p>
<p>所以我重装了一次Ubuntu以确保我之前的安装时正确的，但是我还是不能访问那个额外的分区。之后我问了其他朋友，他们也用Ubuntu。他告诉我说，我必须以Root身份才能挂载那个分区并且要创建一个交换分区（大小是内存的两倍），再把额外的分区挂载为home文件。</p>
<p>When I took a look at the home folder, there were only folders named “dadan” and “lost+found”, and I wondered whether or not it was the other partition. I made a comparison before and after adding some data, then looked at “System Monitor”. And I'm happy, because the amount of free/available space in the partition is different, meaning that the partitioning worked (Figures 1 &amp; 2).</p>
<p>当我看到home文件的时候，只有叫做“dadan”和“lost+found”的两个文件夹，我想知道这是不是就是那个额外的分区。我做了一个比较，向里面加入了一些数据，然后看到“系统监视器”。我很高兴，因为可用空间的数值是不同的，这就意味着分区起作用了（表现1和2）</p>
<p>Figure 1: Before adding data</p>
<p>Figure 2: The amount of free space of /dev/sda1 didn't change, but the size of /dev/sda3 has changed after adding some data to the default document folder.</p>
<p>表现1：在加入数据之前</p>
<p>表现2：/dev/sda1可用空间的数值没有改变，但是/dev/sda3的大小已经在增加了数据到默认文件夹后改变了。</p>
<p>A few days ago, there was a little problem. I was confused about how to restore the upper panel when I deleted it accidentally. On this panel is the Network Manager, which is useful for me to search for available wireless networks around me.</p>
<p>很多天以后，出了点小问题。我不清楚怎样在我不小心删除了上面板以后怎么恢复。在这个面板上有网络管理器，用它搜寻可用的无线服务是很方便的。</p>
<p>I added a blank panel at the top of the screen, then filled it with the Menu Bar, Power Manager, Volume Control, Clock, and Quit. I tried to add Network Manager, but when I searched for it in Add to Panel it was not in the list. Before I found the answer, I had to make a connection in Network Setting and enter it manually.</p>
<p>我添加了一个空白的面板。在我找到解决的办法之前，我不得不在网络选项里面连接网络、手动地数据账号和密码。</p>
<p>sudo /etc/init.d/networking restart</p>
<p>to restart the networking service in terminal mode.</p>
<p>Finally, I found the answer. Actually it was simple to enter:</p>
<p>sudo killall nm-applet</p>
<p>and</p>
<p>nm-applet &amp;</p>
<p>in terminal mode. But the icon for Network Manager didn't appear, even after I did some more trials. Then I searched again on the Web, where I found that I needed to add the Notification Area from the Add to Panel list.</p>
<p>最后，我找到了解决的办法。实际上它是如此简单的两条命令：</p>
<p>sudo killall nm-applet</p>
<p>nm-applet &amp;</p>
<p>（在终端模式）但是网络管理器的图标没出现，即使是我做了更多的尝试之后。然后我再次在网上搜索，我发现原来我需要从面板列表里面添加提示区域。</p>
<p><br />Maybe these technical things are easy to resolve, but not for me as a Linux beginner. Fortunately, the interface for the Ubuntu system is easy to learn, and there are a lot of answers on the Web. I like the challenge of understanding this system because I believe similar technical questions will arise again.</p>
<p>或许这些技术东西很容易解决，但是对我这样的Linux菜鸟来说并不容易。幸运的是，Ubuntu系统的界面学起来很简单，而且网上有很多解决方法。我喜欢这种对Ubuntu系统理解的挑战因为我相信类似的技术问题将时而发生。</p>