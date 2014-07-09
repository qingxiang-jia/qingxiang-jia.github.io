---
layout: post
title: 可爱的Linux还要“建议安装 unrar”
categories:
- Diandian
tags:
- Linux, 
---
lee@lee-desktop:~$ sudo apt-get install rar \\\[sudo\\\] password for lee: 正在读取软件包列表... 完成 正在分析软件包的依赖关系树       读取状态信息... 完成             建议安装的软件包： unrar 下列【新】软件包将被安装： rar 共升级了 0 个软件包，新安装了 1 个软件包，要卸载 0 个软件包，有 44 个软件未被升级。 需要下载 511kB 的软件包。 操作完成后，会消耗掉 1061kB 的额外磁盘空间。 获取：1 http://ubuntu.cn99.com hardy/multiverse rar 1:3.7.1-1 \\\[511kB\\\] 下载 511kB，耗时 1s (258kB/s) 选中了曾被取消选择的软件包 rar。 (正在读取数据库 ... 系统当前总共安装有 121837 个文件和目录。) 正在解压缩 rar (从 .../rar\\\_1%3a3.7.1-1\\\_i386.deb) ... 正在设置 rar (1:3.7.1-1) ... lee@lee-desktop:~$ sudo apt-get install unrar 正在读取软件包列表... 完成 正在分析软件包的依赖关系树       读取状态信息... 完成             下列【新】软件包将被安装： unrar 共升级了 0 个软件包，新安装了 1 个软件包，要卸载 0 个软件包，有 44 个软件未被升级。 需要下载 96.9kB 的软件包。 操作完成后，会消耗掉 246kB 的额外磁盘空间。 获取：1 http://ubuntu.cn99.com hardy/multiverse unrar 1:3.7.8-1 \\\[96.9kB\\\] 下载 96.9kB，耗时 0s (152kB/s) 选中了曾被取消选择的软件包 unrar。 (正在读取数据库 ... 系统当前总共安装有 121852 个文件和目录。) 正在解压缩 unrar (从 .../unrar\\\_1%3a3.7.8-1\\\_i386.deb) ... 正在设置 unrar (1:3.7.8-1) ... lee@lee-desktop:~$