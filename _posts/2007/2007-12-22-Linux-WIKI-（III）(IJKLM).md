---
layout: post
title: Linux WIKI （III）(IJKLM)
categories:
- Diandian
tags:
- Linux

---
I
<br />
<br />IIRC
<br />
<br />If I (Recall|Remember) Correctly
<br />如果我记得没错的话
<br />
<br />IMHO
<br />
<br />In My (Honest|Humble) Opinion
<br />据我看来（坦率地说|以我之愚见）
<br />
<br />Image
<br />
<br />Computer Graphics: an image is a bidimensional array of colored/gray/BW points. It can be stored
<br />
<br />in a large numbre of formats (gif,png,jpg,tiff,bmp...) and can be displayed with an even larger
<br />
<br />number of tools. Web browsers, image viewers or image processing tools, such as The Gimp.
<br />计算机绘图：图像是由彩色/灰色/黑白点组成的二维数组。它可以用大量的格式来保存（
<br />
<br />如gif,png,jpg,tiff,bmp...）同时也可以用更多的工具来显示。网页浏览器，图像观看和处理
<br />
<br />工具，如Gimp。
<br />
<br />Files: an image is an exact copy of a chunk of data. Usually, images are used when creating bootable
<br />
<br />CDs or floppies, by copying an image of a linux kernel on them. Another use is when burning CDs:
<br />
<br />you first create a hard disk image of whatever you want to copy (files or raw audio data) and then
<br />
<br />you copy this image to the CDR.
<br />文件：映像是大块数据的精确拷贝。映像通常在创建可引导光盘或软盘时使用，为了能在
<br />
<br />它们上面拷贝一个Linux内核映像。另一个用法应试是在烧录CD时：你首先创建一个你要
<br />
<br />拷贝的（文件或未加式的音频数据）的硬盘映像，然后将该映像拷到CDR上。
<br />
<br />Interpreters
<br />
<br />a program that can executes commands read from a text file.
<br />能从文本文件中读取并执行命令的程序
<br />
<br />The shell is an interpreter, so are perl, tcl/tk, python, scheme, and to some extent, Java.
<br />Shell就是一个解释程序，因此象perl, tcl/tk, python, scheme和java（在某些程序上）也都是
<br />
<br />。
<br />
<br />A shell (or perl, or any other) script does not need to be compiled, so it is very portable. However
<br />
<br />interpreted languages are usually not as fast as compiled languages such as C, and they depend on
<br />
<br />the presence of the interpreter.
<br />一个Shell（或是perl和其他）脚本不需要被编译，因此它极易移植。然而解释语言通常不
<br />
<br />如编译语言如C语言那么快，并且它们依赖解释程序的存在。
<br />
<br />J
<br />
<br />Java
<br />
<br />&quot;A highly portable object-oriented language whose syntax is based on C++'s&quot;
<br />“一个基于C++语法的高可移植性的面向对象语言”
<br />
<br />Java is currently a very popular language. It is object-oriented and was originally designed by Sun
<br />
<br />Microsystems to provide developers with a very portable language for use on a multitude of devices.
<br />Java是当前非常流行的语言。它是面向对象的，最初被Sun Microsystems设计用来为开发者
<br />
<br />提供可以在多种设备上使用的高可移植性语言。
<br />
<br />Traditionally, a Java program is interpreted by a Java Virtual Machine: a software emulation of a
<br />
<br />standard processing environment (processor, memory, stack, etc.).
<br />Java程序一般是被Java虚拟机解释执行的。Java虚拟机是一个提供标准处理环境的仿真软件
<br />
<br />The JVM is different on every architecture, but the Java program doesn't need any modification or
<br />
<br />compilation when switching from one architecture to another. This makes some Java programs
<br />
<br />exceptionally slow on some occasions, compared to equivalent programs in C++. However, its very
<br />
<br />high degree of portability make it ideal to expand the client-server software concept.
<br />JVM（Java虚拟机）在不同体系结构上都是不同的，但Java程序在一个体系结构切换到另一
<br />
<br />个时却不需要经过任何的修改或编译。这也使得某些Java程序在某些环境下相对于实现相
<br />
<br />同功能的C++程序而言显得异常缓慢。然而，它的高可移植性使之成为扩展client-server（
<br />
<br />客户端-服务器，即我们常说的CS结构）概念的规范。
<br />
<br />The latest advances in the development of Java now include direct compilation, making the
<br />
<br />programs much faster, and expansion in the computer graphics area.
<br />当前Java开发中的最新进展是包含了直接编译功能，以便程序运行的更快，同时扩展了在
<br />
<br />计算机图形领域方面的功能
<br />
<br />joe
<br />
<br />A text editor. ( Actually, it's &quot;Joe's Own Editor&quot; ). joe is based primarily on WordStar, a formerly
<br />
<br />very popular program for MS-DOS.
<br />一种文本编辑器。（实际上，它是“Joe自己的编辑器”）。Joe主要基于WordStar（一个
<br />
<br />以前在MS-DOS下非常流行的程序）开发的。
<br />
<br />See Also Emacs, Recursive.
<br />参见Emacs, Recursive
<br />
<br />K
<br />
<br />Kernel
<br />
<br />The core of a linux system, the kernel is loaded right after your bootloader starts booting linux, and
<br />
<br />starts the system according to your configuration.
<br />Linux系统的核心部分，内核在你的引导程序开始引导Linux之后被引导，然后按照你的配
<br />
<br />置开始运行系统。
<br />
<br />It is the &quot;conductor&quot; of the linux orchestra.
<br />它是Linux系统的“指挥”
<br />
<br />Versions of the Kernel:
<br />内核的版本号：
<br />
<br />* First (major) number: the &quot;Great Number&quot;, that changes once every so often.
<br />* 第一（主）版本号：“重要版本号”，常常会改变。
<br />
<br />* Second (minor)number: the release number.It is even for stable releases and odd for development
<br />
<br />ones.
<br />* 第二（次）版本号：发行版本号，偶数为稳定版本，奇数为开发版本。
<br />
<br />* Third number (patch): the update number, usually bug-fixes, or small upgrades.
<br />* 第三版本号（补丁）：更新版本号，通常是Bug修复或小的升级。
<br />
<br />[ Do NOT (as I once did Smile install a kernel with an odd minor number (i.e. 2.3 and hope it will
<br />
<br />work completely as you expect. Being odd means means this is a development kernel, paving the
<br />
<br />road for the next even, stable release. (i.e. 2.4).
<br />请不要（我就曾经做过）安装次版本号为奇数的内核（如：2.3），并期望它能按你所希望
<br />
<br />的那样完美地工作。奇数版本号意味着那是正在开发的内核，是为下一个稳定版本作好铺
<br />
<br />垫（如：2.4版）。
<br />
<br />L
<br />
<br />Linux
<br />
<br />in the truest sense of the word, &quot;Linux&quot; refers only to the kernel.
<br />从单词确切的意义来说，“Linux”仅仅是指内核。
<br />
<br />What most people people call &quot;Linux&quot; is in fact usually &quot;GNU/Linux&quot;, at least according to the
<br />
<br />Free Software Foundation.
<br />大多数人通常所说的“Linux”实际上是指“GNU/Linux”，起码是按照自由软件基金会
<br />
<br />的说法。
<br />
<br />&quot;Linux&quot; comes from UNIX (of course) and Linus Torvalds, who wrote one of the first free Unix-
<br />
<br />based kernel. It was used by the GNU project as a kernel for their system while the HURD kernel
<br />
<br />was|is in development.
<br />“Linux”来源于UNIX（当然）和Linus Torvalds，编写了第一个自由的类UNIX内核的人。
<br />
<br />它被GNU项目组用来当作他们系统的内核，因为那时他们的HURD内核正在开发中。
<br />
<br />[By the way, some people are still fighting over whether to say lie nucks , or lee nux. Make up your
<br />
<br />mind but choose swiftly , this battle is a bloody mess Wink. Linus Torvalds had to issue a recording
<br />
<br />of how HE said it!]
<br />[顺便说一句，一些人一直在争论它是读成lie nucks还是lee nux。下决心快速地选一个。这
<br />
<br />场论战导致了相当的混乱，以致于Linus Torvalds不得有发布他是如何读它的录音。
<br />
<br />M
<br />
<br />Mailing lists
<br />
<br />There are many (hundreds at least) of user lists, but first browse the archives. Some of those gurus
<br />
<br />don't like answering the same question fifty times.
<br />现在有很多（至少有几百个）用户列表，但是请首先浏览存档。这些邮件列表中的一些专
<br />
<br />家不想五十多次都回答同一个问题。
<br />
<br />They are the closest thing you may find to a &quot;Hot-Line&quot;.
<br />这些都是最近出现的，你也许可以找到一条“热线”
<br />
<br />Manpage
<br />
<br />A specially-formatted file that offers information about a specific command or topic.
<br />一种特定格式的文件，主要提供指定命令或主题的相关信息。
<br />
<br />man ls
<br />
<br />calls the manpage for the command ls, showing syntax, options,etc.
<br />调用命令ls的在线手册，以显示语法，可选项等等。
<br />
<br />Most programs install their own manual in the same place (usually /usr/share/man, though that
<br />
<br />may vary. A variable MANPATH exists and should point to all the directories containing
<br />
<br />manpages).
<br />大多数程序都在同一个地方安装他们自己的手册（通常是/usr/share/man，尽管 也许有可
<br />
<br />能不同。变量MANPATH会指向所有包括在线手册的目录）
<br />
<br />Mount
<br />
<br />A file system is organized in a tree-form, with subdirectories.In order to access another filesystem
<br />
<br />(other partitions, disks,etc) one needs to mount it. That is, specify the type of the filesystem
<br />
<br />(ext3,fat...) and the directory where to put the root of the new filesystem in the directory tree.
<br />文件系统是用带子目录的树形结构组织的。为了访问其他文件系统（另一个分区，磁盘等
<br />
<br />）而需要挂载它。那需要指定文件系统的类型（Ext3，Fat．．．）和目录树中放置新文件
<br />
<br />系统根的目录所在。
<br />
<br />If you have a dos disk called C in which there are the files autoexec.bat and config.sys, then the
<br />
<br />command
<br />如果你有一个被称为C的Dos磁盘，其中包括着autoexec.bat和config.sys文件，然后命令：
<br />mount -t msdos /dev/hda1 /mnt/dos
<br />
<br />will link C:\ to directory /mnt/dos. So
<br />将C:\链接到/mnt/dos目录。于是
<br />ls /mnt/dos
<br />
<br />will give:
<br />将得到：
<br />
<br />autoexec.bat config.sys
<br />
<br />Linux filesystems are usually automatically mounted during the boot phase,starting with the root
<br />
<br />filesystem, and then the others: /usr, /home, etc.
<br />Linux的文件系统通常能在引导阶段自动被挂载，开始是根文件系统，然后是/usr，/home
<br />
<br />等等。
<br />
<br />check your /etc/fstab for more info
<br />查看/etc/fstab以得到更多信息。
<br />
<br />Be careful when changing /etc/fstab, don't mount /usr/local before having mounted /usr, it does
<br />
<br />not make sense...
<br />当改变/etc/fstab时要小心，不要在挂载/usr之前挂载/usr/local，那是不合理的。
<br />
<br />WARNING: The directory called the mount point MUST exist and it MUST ABSOLUTELY be
<br />
<br />EMPTY prior to the mounting operation, or else you will hide files possibly needed for the system's
<br />
<br />stability.
<br />警告：被称为挂载点的目录必须存在，并且它绝对必须在挂载操作前为空，否则为了系统
<br />
<br />的稳定你也必须将文件尽可能的隐藏起来。
<br />
<br />So do NOT mount ANYTHING over / unless you really know what you are doing.
<br />因此不要挂载任何东西在/目录上，除非你确实知道你在干什么。
<br />
<br />If you think you feel the need for such a stunt, take a look at the chroot command.
<br />如果你认为你觉得确实需要那样的话，看一看chroot命令。