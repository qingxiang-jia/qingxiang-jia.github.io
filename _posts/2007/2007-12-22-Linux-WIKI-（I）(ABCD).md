---
layout: post
title: Linux WIKI （I）(ABCD)
categories:
- Diandian
tags:
- Linux, 
---
Thanks to Romain Lerallut who authored the original version for NewbieDoc and to all the
<br />
<br />Newbiedocwriters who've contributed.
<br />感谢NewbieDoc的原作者Romain Lerallut和所有为NewbieDoc作出过贡献的人们。
<br />
<br />A
<br />
<br />access permissions
<br />
<br />A set of permissions associated with every file or directory, (including &quot;special files&quot;), that
<br />
<br />determines who can Read, Write or Execute the file. Only the owner of the file or the super-user
<br />
<br />can modify those permissions.
<br />一组与每个文件或目录相关联的权限，（包括“特殊文件”），以决定谁能读，写或执行
<br />
<br />文件。只有文件的所有者或超级用户才有修改那些权限。
<br />
<br />The format of the access permissions, as shown with ls -l, is a list of 10 symbols:
<br />访问权限的格式，就象用ls -l命令显示的那样，是一个十个符号的列表：
<br />
<br />drwxr-xr-xdrwxr-xr-x
<br />
<br />The first symbol is either - or d, designating whether or not the file in question is actually a
<br />
<br />directory. After that, there are three sets of three symbols each, telling you whether a file (or
<br />
<br />directory) is readable, writable, and executable. The three sets represent the owner, group and
<br />
<br />&quot;everything else&quot; permissions, respectively. For example, the above example represents a file that
<br />第一个符号是-或d，指明当前的文件是否是目录。该符号后面有三组符号，每组由三个符
<br />
<br />号构成，分别告诉你文件（或目录）是否可读、可写和可执行。这三组符号分别对应所有
<br />
<br />者，所在组和所有用户的权限。举个例子，上面的例子表明该文件：
<br />
<br />*
<br />Is a directory
<br />是一个目录
<br />
<br />*
<br />Gives the owner read, write and executable permissions
<br />所有者拥有读，写和执行的权限
<br />
<br />*
<br />Gives the group read and execute permissions
<br />所在组拥有读和执行的权限
<br />
<br />*
<br />Gives everyone else read and execute permissions
<br />其他用户也有读和执行的权限
<br />
<br />See Also Owner, groups.
<br />参见Owner和groups
<br />
<br />AFAIK
<br />
<br />As Far As I Know
<br />就我所知
<br />
<br />ASCII
<br />
<br />American Standard Code for Information Interchange. The standard for representing letters,
<br />
<br />numbers and control characters on 7-bits (8 bits for accentuated character sets).
<br />美国信息交换标准码。用七位比特来描述字母、数字和控制符的标准（8位是增强字符集
<br />
<br />）。
<br />
<br />An ascii text file is a file that can directly be read by basic text editors, such as (cat, more, joe,
<br />ASCII文本文件是可以被基本文本编辑器（如cat,more,joe等）直接阅读的文件。
<br />
<br />See Also Unicode.
<br />参见Unicode
<br />
<br />autocompletion
<br />
<br />A feature offered by most Shells (including but not restricted to bash, tcsh, ksh and especially zsh)
<br />
<br />that allows the shell to complete a command when it can be done unambiguously. It sometimes
<br />
<br />offers a list of the possible completions. Check the Manpage for your shell for exact syntax and
<br />
<br />possible uses. With bash and tcsh, completion is achieved by pressing once on the TAB key. With
<br />
<br />ksh, it's a double strike of the ESC key...check the Manpage.
<br />一个被大多数Shell提供的特性（包括但不仅限于bash,tcsh,ksh和especially zsh），允许Shell
<br />
<br />当一个命令被明白地写出时能补全该命令。有时它还可以提供一个可能的补全列表。查看
<br />
<br />Manpage以找出你所用Shell的准确语法和合适的用法。在bash和tcsh中，补全功能是通过按
<br />
<br />Tab键来实现的。在ksh中，它是通过双击ESC键来实现的....请查阅 Manpage。
<br />
<br />B
<br />
<br />background
<br />
<br />A process is said to be running &quot;in the background&quot; when it is not occupying a terminal. Such
<br />
<br />programs include daemons, as well as other stuff. You can put a running program into the
<br />
<br />background in bash with Ctrl+Z. Bash will list the program name and a number you can use to
<br />
<br />bring the program back to the foreground, with fg &lt;number&gt;.
<br />当一个进程没有占用一个终端时被称为正在“后台”运行，如后台守护及其他程序。你可
<br />
<br />以在bash中用Ctrl+Z快捷键将正在运行的程序切换到后台，也可以用fg &lt;数字&gt;列出后台程
<br />
<br />序名，并将数字所对应的程序切换到前台来。
<br />
<br />binary, binaries
<br />
<br />Binary files are files that are not written in ASCII (human-readable) format, but in succession of
<br />
<br />bytes. Binary files include compile executable files, compressed files (including images), and some
<br />
<br />data files that don't need/allow easy review.(Or that have special requirements: ciphering, size,
<br />
<br />etc...)
<br />二进制文件不是用ASCII（人们可以阅读）码格式编写的，而是由字节组成。二进制文件
<br />
<br />包括已编译的可执行文件，压缩文件（包括图片）和一些不需要/允许可以很方便查看的
<br />
<br />数据文件。（或是有特定需求的：保密，尺寸等）
<br />
<br />BTW
<br />
<br />By The Way
<br />顺便说一句
<br />
<br />C
<br />
<br />C Language
<br />
<br />One of the most powerful computer languages ever invented. Linux is written in C, as well as almost
<br />
<br />all UNIX systems: it is thus very portable among UNIX architectures. In fact, C was invented as a
<br />
<br />language which would make writing an operating system easier, and it was used to create UNIX in
<br />
<br />the first place. A programmer will type C Source code source code in a text editor and then compile
<br />
<br />it into a binary executable form.
<br />众多被发明的功能强大的计算机语言之一。Linux就象所有UNIX系统一样也是用C语言编
<br />
<br />写的。实现上，C语言作为一个语言被发明比操作系统更早，而且它首先被用来创建UNIX
<br />
<br />系统。程序员可以在文本编辑器中编写C源代码，然后把它编译成二进制可执行格式。
<br />
<br />See Also Interpreters.
<br />参见Interpreters
<br />
<br />chown
<br />
<br />The chown command changes the owner of a file or directory to another user. Usage: chown &lt;new
<br />
<br />owner&gt; &lt;file/directory&gt;
<br />chown命令可以将文件或目录的所有者改成另一用户。用法：
<br />chown &lt;新的所有者&gt; &lt;文件/目录&gt;
<br />
<br />Compiler
<br />编译器
<br />
<br />A compiler translates a Source code (ie human readable, ASCII) into binary (machine) code, to be
<br />
<br />executed. GCC is the GNU C Compiler, it is issued with most linux distributions.
<br />编译器将源代码（如人们可读的，ASCII）编译成二进制（机器）代码，以便执行。GCC
<br />
<br />是GNU C的编译器，它被大多数Linux发行版使用。
<br />
<br />D
<br />
<br />daemon
<br />守护程序
<br />
<br />A program that stays in the background, and provides services for users. Daemons are usually
<br />
<br />asleep, and wake up only when a task is assigned to them.
<br />驻留在后台并为用户提供服务的程序。守护程序通常是处于休眠状态，只有当任务被分配
<br />
<br />给它们时才会被唤醒。
<br />
<br />A good example is the printer daemon, that spends its time waiting for documents to send to the
<br />
<br />printer.
<br />一个很好的例子就是打印守护程序，它总是等待文档发往打印机。
<br />
<br />See Also background.
<br />参见background.
<br />
<br />Debian
<br />
<br />Debian is the distribution upon which Ubuntu is based. Like Ubuntu, Debian contains only Free
<br />
<br />software.
<br />Debian是Linux的发行版，Ubuntu就是基于它开发的。象Ubuntu一样，Debian也只包含自由
<br />
<br />软件。
<br />
<br />For any and all info, check out http://www.debian.org
<br />更多信息请参见http://www.debian.org
<br />
<br />There are simultaneously 3 releases of Debian GNU/Linux. One is the &quot;stable&quot;, one the
<br />
<br />accordingly aptly named &quot;unstable&quot;, the middle being held by &quot;testing&quot;. The stable one is one in
<br />
<br />which development is stopped and packages are upgraded only for security-related bug fixing
<br />
<br />purposes. The &quot;unstable&quot; is the development one. In the &quot;testing&quot; release can be found packages
<br />
<br />that have survived 14 days of hard labor in the unstable area and that have been deemed fit for
<br />
<br />service.
<br />Debian GNU/Linux同时存在三个版本。一个是“stable”，一个相对地被称为“unstable”
<br />
<br />，位于中间的称作“testing”。stable 版本是开发已经结束，其中的包只是为于修复安全方
<br />
<br />面的Bug才被升级。unstable版本是正在开发的版本。而在testing版本中的包是在 unstable中
<br />
<br />通过14天的艰苦测试被认为可以提供服务的包。
<br />
<br />Debian was created in 1993 by Ian Murdock. It was named after him and his wife Debra: Deb-ian
<br />
<br />(pronounce it deb-ee-ann).
<br />Debian被Ian Murdock创建于1993年。它是用他和他妻子Debra的名字命名的。Deb-ian（读
<br />
<br />作：deb-ee-ann）。
<br />
<br />Dependencies
<br />
<br />A dependency is a &quot;link&quot; between two packages, mainly when a package is required for another to
<br />
<br />work or to be installed. (debconf is used to configure a number of software. It is written in perl so it
<br />
<br />depends on package perl. Packages depending on debconf, also then depend on perl, which
<br />
<br />depends on.....).
<br />依赖关系是两个包之间的“联系”，主要是一个包在运行和安装时要求另一个包。
<br />
<br />（debconf用于配置许多软件。它是用Perl编写的，因此它依赖于Perl包。那些依赖于
<br />
<br />debconf的包，也依赖Perl包，而它也依赖于......）。
<br />
<br />Dependencies also refer to conflicting software or versions. You can't easily remove a package if
<br />
<br />other packages depend on it. No package management programs will allow this to happen without a
<br />
<br />command to ignore dependencies.
<br />依赖关系也指明软件或版本冲突。你不能很轻易地删除一个包，如果其他包也依赖它的话
<br />
<br />。没有任何包管理软件会允许这样做，也没有任何命令会忽略依赖关系。
<br />
<br />See Also Packages.
<br />参见Packages。
<br />
<br />/dev
<br />
<br />/dev contains &quot;pseudo files&quot; that are really gateways into peripherals. Most peripherals are &quot;talked
<br />
<br />to&quot; by one or more /dev/* files. Among them:
<br />/deb目录包含指向外部设备的“伪文件”。大多数外设被映射成一个或更多/dev/文件。在
<br />
<br />它们中：
<br />
<br />*
<br />/dev/fd0 = The first floppy disk drive (MS-DOS floppy ASmile
<br />/dev/fd0 = 第一个软盘驱动器（MS-DOS 软盘 A盘）
<br />/dev/fd1 = The second floppy disk drive (MS-DOS floppy BSmile
<br />/dev/fd1 = 第二个软盘驱动器（MS-DOS 软盘 B盘）
<br />
<br />*
<br />/dev/hd[a-d] = IDE drives...
<br />/dev/hd[a-d] = IDE 驱动器...
<br />
<br />/dev/hda = controller 1 master drive
<br />/dev/hda = 控制器1主盘
<br />/dev/hdb = controller 1 slave drive
<br />/dev/hdb = 控制器1从盘
<br />/dev/hdc = controller 2 master drive
<br />/dev/hdc = 控制器2主盘
<br />/dev/hdd = controller 2 slave drive
<br />/dev/hdd = 控制器2从盘
<br />
<br />to get to the partitions, append partition number:
<br />分区后，出现分区数：
<br />/dev/hda1 /dev/hdb6 /dev/hdd19
<br />
<br />*
<br />/dev/sc[a-...] = SCSI drives
<br />/dev/sc[a-...] = SCSI驱动器
<br />
<br />/dev/scd = SCSI device ID 4 (&lt;== is this right?)
<br />/dev/scd = SCSI驱动器ID号为4（&lt;==对吗？）
<br />
<br />to get to the partitions, append partition number:
<br />分区后，出现分区数：
<br />/dev/scd7 /dev/scd13
<br />
<br />*
<br />depending on your sound driver,these devices are used to send/retrieve sound data:
<br />依赖你的声音驱动器，这些设备被用于发送/取回声音数据：
<br />
<br />/dev/audio
<br />
<br />/dev/dsp
<br />
<br />/dev/mixer
<br />
<br />/dev/sequencer
<br />
<br />/dev/tty* = remote terminal interface
<br />/dev/tty* = 远程终端接口
<br />
<br />/dev/tty?? shows up with the `w` command when you log in via hardwired terminal
<br />当你用线连接终端时，/dev/tty?? 会显示“w”。
<br />
<br />*
<br />/dev/pts/* = pseudo-tty - ssh or (horrors!) telnet interface
<br />/dev/pts/* = pseudo-tty -ssh或telnet接口
<br />
<br />/dev/pts/* lets you interact with a command shell just like a real tty (above)
<br />/dev/pts/* 让你通过命令行象真的tty一样与机器进行交互。
<br />
<br />*
<br />/dev/mouse = your mouse COM port
<br />/dev/mouse = 你的鼠标COM口
<br />
<br />Some of those files are symbolic links to others, for example:
<br />该文件有些是软链接到其它设备接口文件的，如：
<br />
<br />/dev/mouse -&gt; /dev/psaux for PS/2 mice
<br />/dev/mouse -&gt; /dev/psaux PS/2鼠标
<br />
<br />/dev/cdrom -&gt; /dev/hdc if you have an IDE CD-Rom drive
<br />/dev/cdrom -&gt; /dev/hdc 如果你有一个IDE CD-ROM驱动器
<br />
<br />And also many others that I don't know and that you won't have to know about unless you do wild
<br />
<br />things with your linux box Wink.
<br />还有我不知道的许多其他方面，你也不需要知道除非你要用你的Linux做更多的事。（box
<br />
<br />Wink我不知道要怎么翻，还是老规矩，有请高手）
<br />
<br />Distribution, distro, dists
<br />
<br />&quot;Linux&quot; does not exist by itself. A distribution is
<br />“Linux”本身并不存在。一个发行版是指
<br />
<br />1.
<br />a Linux Kernel, and
<br />一个Linux内核
<br />
<br />2.
<br />applications (software).
<br />应用程序（软件）。
<br />
<br />The kind of software, the price of it (or lack thereof), details of the implementation, all depend on
<br />
<br />the distribution.
<br />软件的种类，价格（或没有），实施细节全依赖于发行版。
<br />
<br />Among them: Debian, Red Hat, SuSe, Slackware, Mandrake ... and lots of others.
<br />它们包括：Debian，Red Hat, SuSe, Slackware, Mandrake ... 以及其他很多。
<br />
<br />They mostly differ by the tools they offer to manage and or install the system.
<br />它们提供的用于管理或安装系统的工具大部分是不同的。
<br />