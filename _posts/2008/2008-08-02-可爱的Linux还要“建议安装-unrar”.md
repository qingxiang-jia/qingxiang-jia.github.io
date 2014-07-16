---
layout: post
title: 可爱的Linux还要“建议安装 unrar”
categories:
- Diandian
tags:
- Linux

---
lee@lee-desktop:~$ sudo apt-get install rar
<br />[sudo] password for lee:
<br />正在读取软件包列表... 完成
<br />正在分析软件包的依赖关系树&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<br />读取状态信息... 完成&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<br />建议安装的软件包：
<br /> unrar
<br />下列【新】软件包将被安装：
<br /> rar
<br />共升级了 0 个软件包，新安装了 1 个软件包，要卸载 0 个软件包，有 44 个软件未被升级。
<br />需要下载 511kB 的软件包。
<br />操作完成后，会消耗掉 1061kB 的额外磁盘空间。
<br />获取：1 http://ubuntu.cn99.com hardy/multiverse rar 1:3.7.1-1 [511kB]
<br />下载 511kB，耗时 1s (258kB/s)
<br />选中了曾被取消选择的软件包 rar。
<br />(正在读取数据库 ... 系统当前总共安装有 121837 个文件和目录。)
<br />正在解压缩 rar (从 .../rar_1%3a3.7.1-1_i386.deb) ...
<br />正在设置 rar (1:3.7.1-1) ...
<br />lee@lee-desktop:~$ sudo apt-get install unrar
<br />正在读取软件包列表... 完成
<br />正在分析软件包的依赖关系树&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<br />读取状态信息... 完成&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<br />下列【新】软件包将被安装：
<br /> unrar
<br />共升级了 0 个软件包，新安装了 1 个软件包，要卸载 0 个软件包，有 44 个软件未被升级。
<br />需要下载 96.9kB 的软件包。
<br />操作完成后，会消耗掉 246kB 的额外磁盘空间。
<br />获取：1 http://ubuntu.cn99.com hardy/multiverse unrar 1:3.7.8-1 [96.9kB]
<br />下载 96.9kB，耗时 0s (152kB/s)
<br />选中了曾被取消选择的软件包 unrar。
<br />(正在读取数据库 ... 系统当前总共安装有 121852 个文件和目录。)
<br />正在解压缩 unrar (从 .../unrar_1%3a3.7.8-1_i386.deb) ...
<br />正在设置 unrar (1:3.7.8-1) ...
<br />
<br />lee@lee-desktop:~$
<br />