---
layout: post
title: Linux WIKI （IV）(OPQRS)
categories:
- Diandian
tags:
- Linux

---
O
<br />
<br />Open Source
<br />
<br />A general term that refers to software that has its source code included so that the consumer can
<br />
<br />modify the software if required. It is usually used as a synonym for Free Software.
<br />一个常用名词是指软件包括其源代码，以便客户可以在需要时修改该软件。它通常是自由
<br />
<br />软件的同义词。
<br />
<br />P
<br />
<br />/proc/*
<br />
<br />Pseudo-directory structure acting as gateway to communicate with processes and other 'behind-the
<br />
<br />-scenes' bowels such as networking, memory, etc.
<br />伪目录结构作为网关与进程和其他后台内部程序如网络、内存等进行通讯。
<br />
<br />Those files don't really exist; when read, the system reports info, and some items, when written to,
<br />
<br />change system behavior. Pretty cool!
<br />哪些文件并不真正存在；当被读时，系统报告信息和其他项，当被写时，改变系统行为。
<br />
<br />相当的酷！
<br />
<br />* /proc/$$ = info about current shell (aka $$) including commandline, present directory,
<br />
<br />environment vars, etc
<br />* /proc/$$ = 当前Shell（aka $$)的相关信息，包括命令行，当前目录和环境变量等
<br />
<br />* /proc/self/ = symlink to current process info
<br />* /proc/self/ = 到当前进程信息的软连接
<br />
<br />* /proc/sys/net/* = ...
<br />
<br />* /proc/pci: info about PCI devices
<br />* /proc/pci: PCI设备相关信息
<br />
<br />* /proc/interrupts: for IRQ monitoring
<br />* /proc/interrupts: 中断监视
<br />
<br />* ...
<br />
<br />Packages
<br />
<br />Linux software typically come either in tarballs or in packages.
<br />通常Linux软件是以Tarballs或包的形式出现的。
<br />
<br />Most distributions prefer the package form for two reasons:
<br />大多数发行版都喜欢用包，原因有两点：
<br />
<br />* It is easier to track what is installed, if it only means checking which packages (and versions).
<br />* 如果它只表示着哪个软件（和版本）的话，能更容易跟踪安装了什么。
<br />
<br />(This is very important because, in the Linux world, software changes often)
<br />（这是非常重要的，因为在Linux世界里软件经常改变。）
<br />
<br />* It is a very convenient way to check that dependencies are met.
<br />* 它提供了更方便检查合适依赖关系的途径。
<br />
<br />Package management
<br />
<br />On Ubuntu systems, use synaptic, aptitude, apt-get or dpkg.
<br />在Ubuntu系统中，使用synaptic, aptitude, apt-get或dpkg。
<br />
<br />Ubuntu and Debian packages have the extension .deb , and RedHat 's have .rpm.
<br />Ubuntu和Debian包有着.deb的扩展名，而RedHat则是.rpm。
<br />
<br />Partition
<br />
<br />A partition is a chunk of hard disk on which a filesystem can be built.
<br />分区是硬盘上可以创建文件系统的一块区域。
<br />
<br />A hard disk can have many partitions , each with its own filesystem. This makes it possible to have
<br />
<br />two or more operating systems coexist on the same hard disk drive, each one living in its own
<br />
<br />partition(s).
<br />一个硬盘可能有许多的分区，每个都可以有自己的文件系统。这使得同一个硬盘上可能拥
<br />
<br />有两个或两个以上的操作系统，且每个都在它自己的分区里。
<br />
<br />&quot;Partitioning a hard drive&quot; means separating it into partitions. There are a number of tools to do
<br />
<br />this, among them the native Linux tools&quot;fdisk&quot; and &quot;cfdisk&quot;, as well as the controversial &quot;Partition
<br />
<br />Magic&quot; for Windows.
<br />“硬盘分区”意味着将它分成几个分区。有很多工具可以做到这一点，在它们中Linux自
<br />
<br />带的工具是&quot;fdisk&quot;和&quot;cfdisk&quot;，类似于Windows环境中的&quot;Partition Magic&quot;。
<br />
<br />Linux requires at least two partitions: one is the linux swap partition, (usually twice the size of the
<br />
<br />RAM) and the other is the ext3 root filesystem. However it is sometimes recommended to mount
<br />
<br />/usr, /home, and other directories on other partitions than the one containing the root FS.
<br />Linux要求至少有两个分区：一个是Linux的交换分区（通常是RAM的两倍），另一个是
<br />
<br />Ext3格式的根文件系统。然而，相对于一个根文件系统而言，人们常常会被建议在其他分
<br />
<br />区中挂载/usr、/home和其他目录。
<br />
<br />path
<br />
<br />The list of directories from the root directory (absolute path) or from any directory (relative path) to
<br />
<br />a given file: /usr/bin/vi is the absolute path of vi. When the current directory is /usr the relative
<br />
<br />path of vi is ./bin/vi.
<br />从根目录（绝对路径）或从任何目录（相对路径）到给定文件的目录列表：/usr/bin/vi就
<br />
<br />是一个到vi相对路径。如果当前目录是/usr，那么vi的相对路径就是./bin/vi了。
<br />
<br />People also refer to the PATH, which is a list of directories in which commands will run without
<br />
<br />needing to use the full, absolute path above. For example, if /usr/bin wasn't listed in your PATH,
<br />
<br />you would need to use the command /usr/bin/vi instead of simply vi. Your PATH is an
<br />
<br />environment variable for your shell, and changing it depends on the shell you are using.
<br />人们也指定PATH变量，包括着命令的目录列表，以便不必使用完全绝对路径。举个例子
<br />
<br />，如果/usr/bin目录没有列在你的PATH变量中，那么你将需要使用 /usr/bin/vi来代替简单
<br />
<br />的vi命令。你的PATH变量是你SHELL中的一个环境变量，对它的改变取决于你所使用
<br />
<br />Shell。
<br />
<br />See Also Shell.
<br />参见Shell
<br />
<br />PERL
<br />
<br />Practical Extraction and Report Language, or Pathological Eclectic Rubbish Lister ; both names are
<br />
<br />endorsed by its author, Larry Wall.
<br />“Practical Extraction and Report Language”或“Pathological Eclectic Rubbish Lister”这两个
<br />
<br />名字都被它的作者Larry Wall肯定。
<br />
<br />Sometimes referred to as &quot;The administrator's swiss army chainsaw&quot;
<br />有时被称为“管理员的瑞士军刀”
<br />
<br />Perl is a popular interpreted language, that is used very often to build system administration tools,
<br />
<br />such as debconf, or parts of some servers.
<br />Perl是一种流行的解释语言，它常被用于建立系统管理工具，如debconf，或某些服务的部
<br />
<br />分。
<br />
<br />Processes
<br />
<br />A process is the way the linux kernel represents programs that are running or are in temporary
<br />
<br />standby.
<br />进程是Linux内核表现正在运行或暂时挂起程序的一种方式。
<br />
<br />Processes are identified by a unique number called PID.They are also characterized by their owner,
<br />
<br />and their priority.
<br />进程由一个唯一的被称为PID的数字来标识。他们也被他们的所有者或优先级描述。
<br />
<br />Check the current processes with ps or ps aux for all of them.
<br />检查当前进程可以用ps或用ps aux来检查全部进程。
<br />
<br />Proprietary
<br />
<br />The approximate opposite of Open Source and Free Software. A data format is proprietary when its
<br />
<br />specifications are not made public.
<br />几乎是开源和自由软件反义词。当一个数据格式没有被公开时它就是私有的了。
<br />
<br />Software is said to be proprietary when access to the source is not granted, or only to a selected
<br />
<br />panel of reviewers. Proprietary software is usually very expensive, compared to Open Source, and is
<br />
<br />often less tested.
<br />当软件的源代码不允许或只允许一些被挑选的评论家查看时它就被称为是私有软件了。私
<br />
<br />有软件相对于开源软件来说通常十分贵，并且常常测试较少。
<br />
<br />R
<br />
<br />Recursive
<br />
<br />An acronym in which the first word is the acronym itself. For example:
<br />用自身单词的第一个字母来做为自己的首字母组合词。如：
<br />
<br />GNU: Gnu is Not Unix
<br />
<br />JOE: Joe's Own Editor
<br />
<br />Wine: Wine Is Not an Emulator
<br />
<br />and my favorite:
<br />和我的极爱：
<br />
<br />HURD: Hird of Unix-Replacing Daemons
<br />
<br />HIRD: Hurd of Interfaces Representing Depth
<br />
<br />[&quot;We have here, to my knowledge, the first software to be named by a pair of mutually recursive
<br />
<br />acronyms.&quot;], see here
<br />[“这里，第一个软件用首字母组合词相互递归的一部分来命令”]，参见这里
<br />
<br />Regular expressions
<br />
<br />One of the most powerful features of any Unix system is the &quot;regular expression&quot; (also called
<br />
<br />&quot;regexp&quot; ). It is a series of special characters that are used to design patterns, that can be used to
<br />
<br />build lists of strings (usually but not always filenames). Those lists can then be used by most
<br />
<br />command line tools. Also see wildcard...
<br />在Unix系统中非常有特色之一就是“命名规则”（也叫“RegExp”）。它由一系列特点的
<br />
<br />字符组成的，用于创建字符串列表（通常但不仅限于文件名）的设计规范。那些列表可以
<br />
<br />被大多数命令行工具使用。参见wildcard...
<br />
<br />Root
<br />
<br />1) Administrator aka &quot;superuser&quot;
<br />1) 管理员也称“超级用户”
<br />
<br />The root account is the all-powerful maintenance account. It can read/modify/delete any and all
<br />
<br />files on the system. It is used when installing soft/hardware, for maintenance tasks, and some
<br />
<br />processes are run under root UID.
<br />root帐号是拥有所有维护权限的帐号。它能读/修改/删除系统上的任意或全部文件。当安
<br />
<br />装软/硬件时使用该帐号，以便维护任务或一些在根用户UID下运行的进程。
<br />
<br />One runs a command as &quot;root&quot; by typing “sudo COMMAND”at a normal user's shell prompt
<br />
<br />and then typing their own password.
<br />作为根用户运行一个命令，在一般用户的Shell提示符中键入：“sudo COMMAND”并输入
<br />
<br />他们自己的密码。
<br />
<br />Warning
<br />警告
<br />
<br />DO NOT use the root account when you can use a normal user's. Even if you are the only user, if
<br />
<br />you don't need to do specifically administration tasks, then do your work as a normal user.
<br />
<br />Otherwise, you run the risk of deleting everything on your computer. The root account is very
<br />
<br />powerful.
<br />在你可以使用一般用户不要使用根用户，甚至你是唯一的用户，如果你不需要运行特定的
<br />
<br />管理员任务，那么作为一般用户来进行你的工作。否则你将冒着在你计算机上删除任何东
<br />
<br />西的危险。root帐号的权利是非常大的。
<br />
<br />2) filesystem aka &quot;/&quot;
<br />2) 文件系统也称为“/”
<br />
<br />The root file system is the first to be mounted. It is the root of the file system tree (ergo , the name).
<br />
<br />Other filesystems are mounted on sub-directories of / (eg /usr, /home and of course /mnt ). The
<br />
<br />kernel needs to be able to mount a root file system (NEEDS ?? CHECK), so its location is specified
<br />
<br />in lilo.
<br />根文件系统是第一个被挂载的。它是文件系统树的根（如其名所示）。其它文件系统作为
<br />
<br />/的目录被挂载上来（如 /usr，/home和当然的/mnt）。内核需要挂载一个根文件系统（需
<br />
<br />要？检查），因此它的位置在lilo中就被指定了。
<br />
<br />RTFM
<br />
<br />Read The Fine Manual
<br />请读详细手册
<br />
<br />also sometimes RFD: Read the Fine Doc.
<br />有时也写作RFD：请读详细文档
<br />
<br />See Also Manpage.
<br />参见Manpage
<br />
<br />S
<br />
<br />SGML
<br />
<br />See Standard Generalized Markup Language.
<br />参见Standard Generalized Markup Language
<br />
<br />Standard Generalized Markup Language
<br />
<br />A powerful markup language for writing documents. HTML is a compact, more specific form of
<br />
<br />SGML. For information, see Docbook.org
<br />一个用于编写文档的功能强大的标识语言。HTML是一种简单的，有着更多特定格式的
<br />
<br />SGML。更多信息参见Docbook.org
<br />
<br />See Also Extensible Markup Language.
<br />参见Extensible Markup Language
<br />
<br />Shell
<br />
<br />The shell is an interpreter. It can either be used as a command line interpreter for a terminal, or as a
<br />
<br />shellscript interpreter. A command-line shell is started each time a [pseudo-]terminal is created
<br />
<br />(using xterm for instance). The type of shell for a certain user can be set by editing /etc/passwd: the
<br />
<br />last field of the user's line is the shell. Change from /usr/bin/bash to /usr/bin/zsh, if you like but
<br />
<br />make sure the file can be found at that place, since there is no fall-back.
<br />Shell是一个解释程序。它即能作为终端的命令行解释程序，也可作为Shell脚本解释程序。
<br />
<br />一个命令行Shell在每次打开一个[伪]终端（比如说使用xterm）时开始运行。某个特定用户
<br />
<br />所使用的Shell类型可以通过编辑/etc/passwd中用户行的最后一段来指定。如果你喜欢可以
<br />
<br />将/usr/bin/bash改成/usr/bin/zsh，不过请确定该文件能在指定位置找到，因为无法回退。
<br />
<br />There are many different kinds of shells and choosing one is a matter of taste. Most Linux
<br />
<br />distributions offer the bash (Bourne Again SHell) as default but you can see also the csh (C-SHell),
<br />
<br />tcsh (exTended C-SHell), the ksh (Korn SHell), etc.
<br />现在有许多不同的Shell，只需选择其中之一来体验。大多数Linux发行版提供bash（Bourne
<br />
<br />Again SHell）作为缺省Shell，不过你也可以使用 csh (C-SHell), tcsh (exTended C-SHell), the
<br />
<br />ksh (Korn SHell)等等。
<br />
<br />Shell programming using scripts is a very powerful tool for an administrator, since it was initially
<br />
<br />designed for file processing using the many command-line UNIX programs (cat, ls, ps, more, head,
<br />
<br />tail, awk, sed, etc.)
<br />通过使用脚本，Shell程序对管理员来说是十分强大的工具，因为它最初就是作为处理大量
<br />
<br />命令行的Unix程序文件而被设计的。
<br />
<br />soft-link
<br />
<br />See Symlink.
<br />参见Symlink。
<br />
<br />Source code
<br />
<br />A human readable text file. It can either be compiled into an executable program , or it can be
<br />
<br />interpreted. Being able to read the source code gives de facto complete knowledge of the program,
<br />
<br />in order to understand it, de-bug it, replicate it, etc.
<br />一种人们可读的文本文件。它要么可以编译成一个可执行文件，要么能被解释执行。可以
<br />
<br />读源代码实际上能够对程序形成完整的概念，以便理解它，调试它和重现它等等
<br />
<br />See Also Proprietary, Open Source.
<br />参见Proprietary, Open Source
<br />
<br />Symlink
<br />
<br />On Windows it's called a shortcut; on Macintosh, it's an alias. A symbolic link is a directory entry
<br />
<br />that points to some other directory entry (directory or file).
<br />在Windows中它被称为快捷方式；在Macintosh，它是别名。一个符号链接是一个指向其他
<br />
<br />目录项（目录或文件）的目录项。
<br />
<br />These are very handy. If you have several versions of a project or file, you can
<br />它是非常方便的。如果你有一个项目或文件的几个不同版本，你可以
<br />
<br />ln -s actual-item-being-worked-on current
<br />
<br />to be able to refer to &quot;current&quot; instead of the actual item. If the version changes, just update which
<br />
<br />item your link &quot;current&quot; should point to. Then just keep using &quot;current&quot; so you'll never have to
<br />
<br />change your typing habits. Very slick!
<br />用“current（当前）”来代替现在的项。如果版本改变了，只需要更新你的“current”链
<br />
<br />接的指向就行了。然后只需要保持使用“current”就可以了。因此你永远也不需要改变你
<br />
<br />的输入习惯了。非常灵活！
<br />
<br />A symlink is a standalone file, removing it will NOT remove the file it points to.
<br />一个symlink链接是一个独立的文件，删除它不能删除它所指向的文件
<br />
<br />See Also Hard link.
<br />参见硬链接。