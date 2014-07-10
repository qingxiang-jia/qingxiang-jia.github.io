---
layout: post
title: Linux WIKI （II）(EFGH)
categories:
- Diandian
tags:
- Linux, 
---
E
<br />
<br />Emacs
<br />
<br />One of the most famous text-editors in the UNIX world. Part of the GNU project, there is a text-
<br />
<br />only version as well as a graphical one, with LOTS of &quot;plugins&quot; available to customize your own
<br />
<br />version. Emacs has the reputation of being able to do everything, up to but not excluding being the
<br />
<br />proverbial kitchen sink. Keep in mind that it is a fairly difficult editor to use, especially with all of
<br />
<br />the plugins installed. Many people stay away from Emacs, using the argument that an editor's job is
<br />
<br />to let you edit, and programs should do one thing well instead of everything.
<br />UNIX世界著名的文本编辑器之一。GNU项目的一部分，它既有纯文本版本也有图形版本
<br />
<br />，并且拥有大量“插件”以便定制出你自己的版本。Emacs甚至被激进现实主义者宣称其
<br />
<br />能够做任何事而闻名天下。（这一句太不好翻了，还是有请高手）但请牢记，它是一个用
<br />
<br />起来相当困难的编辑器，尤其是当所有插件都被安装之后。很多人都不再使用Emacs。编
<br />
<br />辑器的工作是在于编辑，程序应该做好它应做的一件事，而不是每一件事。
<br />
<br />See Also joe.
<br />参见joe
<br />
<br />Ext3 FS
<br />
<br />Third-Extended Filesystem, currently the standard filesystem used in Linux.
<br />第三扩展文件系统，当前作为Linux文件系统的标准。
<br />
<br />See Also Filesystem.
<br />参见文件系统
<br />
<br />F
<br />
<br />FAT
<br />
<br />The standard name for the family of filesystems that use Microsoft's File Allocation Table format.
<br />
<br />For example, FAT16 is the old MS-DOS file system, VFAT is the filesystem introduced with
<br />
<br />Windows 95, allowing filenames longer than 8 characters, and FAT32 is the current filesystem for
<br />
<br />Windows systems, with some improvements on VFAT. Windows NT uses a different filesystem
<br />
<br />known as NTFS instead of a FAT system. Of course, all of these filesystems can be accessed from
<br />
<br />Linux, as long as you use the right tools (even though writing to NTFS filesystems may be risky).
<br />文件系统中使用微软文件定位表（File Allocation Table）格式的标准名称。例如：FAT16是
<br />
<br />老的MS-DOS文件系统，VFAT是Windows 95引进的文件系统，允许文件名超过8个字符，
<br />
<br />FAT32是当前Windows操作系统使用的文件系统，在VFAT系统上做了一些扩展。Windows
<br />
<br />NT使用了不同的文件系统NTFS来代替FAT系统。当然所有的这些文件系统都能被Linux访
<br />
<br />问，只要你使用正确的工具（尽管对NTFS文件系统进行写操作也许是危险的）。
<br />
<br />See Also Filesystem.
<br />参见文件系统
<br />
<br />Filesystem
<br />
<br />a way of storing files on a medium which can be hard drives, floppies, cdroms etc,etc...
<br />在介质（如硬盘、软盘、CD-ROM等）上保存文件的方式。
<br />
<br />ext3 (3nd Extended) is currently the &quot;native&quot; FS for linux.
<br />ext3（第三扩展）是Linux当前“自带”的文件系统。
<br />
<br />ReiserFS is a recent filesystem, designed for both speed and survivability.
<br />ReiserFS是最新的文件系统，主要基于速度和安全性设计的。
<br />
<br />fat and vfat are the linux names for the standard Microsoft(r) Windows(r) filesystems: fat16 (fat) and
<br />
<br />fat32 (vfat).
<br />fat和vfat是Linux对微软windows标准文件系统的命名方式：fat16（fat）和fat32（vfat）。
<br />
<br />iso9660 is usually the standard for CD-ROMs.
<br />iso9660通常是CD-ROM的标准。
<br />
<br />smb,nfs,... are network filesystems, that allow computers to share data. 'smb' is Microsoft(r)'s well-
<br />
<br />known 'Network Neighborhood'.
<br />smb，nfs，...是网络文件系统，允许计算机之间共享数据。'smb'就是微软的众所周知的“
<br />
<br />网上邻居”。
<br />
<br />proc,dev,... are also [special] filesystems.
<br />proc，dev，...也是（特殊的）文件系统。
<br />
<br />Linux supports a great number of other file systems, at least in reading but most of them in
<br />
<br />read/write.
<br />Linux支持大量其他文件系统，至少是可以读取其中内容，但大多数是可以对其进行读写
<br />
<br />的。
<br />
<br />Free software
<br />
<br />free is taken in the &quot;freedom&quot; sense.
<br />free其实是“自由（freedom）”的意思。
<br />
<br />It is a way of creating and distributing software with the source code and with the right to modify,
<br />
<br />upgrade and (re-)sell it as one sees fit to do, as long as the license (usually the GNU Public License
<br />
<br />(GPL)) comes along.
<br />这是一种创建和发布软件的方式，软件带源代码，并且只要人们觉得必要，许可证（通常
<br />
<br />是GNU公共许可证（GPL））许可，他们就拥有修改，更新和（重新）销售的权利。
<br />
<br />The term Open Source is also used to refer to software that is Free not because of ideological
<br />
<br />beliefs, but because it is a convenient way to develop programs. See http://www.opensource.org&gt;.
<br />术语开放源代码也通常指明软件是自由的，不是因为空想的理念，而是因为它对程序开发
<br />
<br />而言是一种适合的方式。参见http://www.opensource.org
<br />
<br />Open Source software includes but is not restricted to Free Software. It is also easier to convince
<br />
<br />software companies to release their sources with the term 'Open Source' than with 'Free Software',
<br />
<br />or so is it thought.
<br />开源软件包括但不仅是自由软件，术语“开放源代码”比“自由软件”也更容易说服软件
<br />
<br />公司开放它们的源代码或它们的编程思路。
<br />
<br />check http://www.gnu.org
<br />请查阅http://www.gnu.org
<br />
<br />FWIW
<br />
<br />For What It's Worth
<br />不论真假；随便说说
<br />
<br />G
<br />
<br />GNU
<br />
<br />Recursive acronym for &quot;GNU's Not Unix&quot;
<br />递归定义。是“GNU's Not Unix”的首字缩写。
<br />
<br />The GNU project was initiated in 1984 by Richard M Stallman, a software developer at MIT's AI
<br />
<br />Lab. Its goal is to provide high-quality Free Software.
<br />GNU项目是于1984年麻省理工AI实验室里的一名软件开发者Richard M Stallman创建的。该
<br />
<br />项目的目标是提供高质量的自由软件。
<br />
<br />groups
<br />
<br />User groups are a feature inherited from UNIX. Groups exist mostly so that resources can be
<br />
<br />shared between users belonging to the same group. For example, while files for our project are
<br />
<br />generally owned by the authors, they are part of the newbiedoc group so that any of us can work
<br />
<br />with them.
<br />用户组是从UNIX继承下来的特性。之所以需要组是为了让属于同一组的用户能够共享资
<br />
<br />源。举个例子，在我们项目中每个文件的所有者通常都是作者本人，它也是Newbiedoc组
<br />
<br />的成员，因此我们中的任何人都可以工作在它们上面。
<br />
<br />See Also access permissions.
<br />参见access permissions
<br />
<br />H
<br />
<br />Hard link
<br />硬链接
<br />
<br />To the contrary of the symlink (symbolic link), here the actual data on disk is pointed to by more
<br />
<br />than one directory entry.
<br />它是相对于symlink（符号链接，其实也就是我们常说的软链接）而言的，表示超出一个的
<br />
<br />目录项指向磁盘上同一块真实数据。
<br />
<br />A symbolic link is merely a file that refers to another file; a hard link is actually the same exact
<br />
<br />information, located at the same spot on the disk.
<br />符号链接仅仅只是一个指向另一个文件的文件；而硬链接则实际上是被定位在磁盘相同点
<br />
<br />上的完全相同的信息。
<br />
<br />With a hard link, you can pick any one of the instances of the file, and delete all the rest, and it'll still
<br />
<br />exist; with symbolic links, you can delete the target file and then all the symbolic links to it will point
<br />
<br />to a non-existent file!
<br />使用硬链接，你可以选择文件的任何一个实例并删除所有其他的，该仍然存在；而用符号
<br />
<br />链接，当你删除了目标文件之后，那所有的软链接将指向一个并不存在的文件！
<br />
<br />But it's much easier to distinguish between an itty-bitty symbolic link and the target file, than the
<br />
<br />original doc and any other hard link to it. In fact, it's impossible, since they are the exact same thing!
<br />但是，它也使得区分符号链接和目标文件比起区分原始文件和其他硬链接来得容易。实际
<br />
<br />上，那是不可能的，因为它们（原始文件和其他硬链接）是完全相同的。
<br />
<br />Hard links are becoming more and more obsolete, in favor of soft links. I strongly suggest you use
<br />
<br />symlinks, unless you know what you are doing.
<br />相对于软链接，硬链接被用得越来越少了。我强烈建议你使用符号链接，除非你知道你正
<br />
<br />在做什么。
<br />
<br />(the reference count , ie the number of hard links can be seen on the second column of an ls -l.
<br />（索引计数，也就是说在使用ls -l时可以在第二列看出硬链接数
<br />
<br />If you delete a file with a &gt;1 reference count, it means the data is still stored somewhere, and
<br />
<br />accessible through another hard link,
<br />如果你删除了一个索引计数a &gt;1的文件，那就意味着数据仍然被保存在磁盘的某个地方，
<br />
<br />并可以通过另一个硬链接进行访问。
<br />
<br />if the reference count ==1, and you delete the file, the data will be lost and the space will actually be
<br />
<br />freed.
<br />如果索引计数等于1，而你又删除了该文件，那么数据将丢失同时数据所占空间将被释放
<br />
<br />。
<br />
<br />Don't mention reference counts smaller than 1 they are bad news Smile
<br />不要说你的索引计数小于1，那将是个坏消息。一笑。
<br />
<br />HTH
<br />
<br />Hope This Helps
<br />希望得到帮助