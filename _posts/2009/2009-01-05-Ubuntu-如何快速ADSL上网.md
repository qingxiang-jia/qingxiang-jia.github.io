---
layout: post
title: Ubuntu 如何快速ADSL上网
categories:
- Diandian
tags:
- Linux

---
至于配置，帮助文件里面说得很清楚。我重点要说的是网城配置以后如何简单打开链接和断开连接。
<br />一般我们配置的时候默认的都是开机就联网，但是我的电脑开机的时候不能够顺利联网，那么就需要我们到终端输入命令，每次都输入命令比较麻烦，有一个简单的办法。
<br />打开连接和断开连接的命令分别是：sudo pon dsl-provider 和 sudo poff dsl-provider，在桌面上右键▸创建启动器，
<img src="http://m3.img.srcdd.com/farm5/d/2012/0627/10/3B09BB9B27FBAF5300CACAEA865229F5_B500_900_422_238.PNG" />
<br />类型选择“终端中的应用程序”，名称随便，命令就是刚才的两条，注释随意。完成以后，下次要断开或者启动连接直接双击就好了，比WINDOWS下方便100倍。