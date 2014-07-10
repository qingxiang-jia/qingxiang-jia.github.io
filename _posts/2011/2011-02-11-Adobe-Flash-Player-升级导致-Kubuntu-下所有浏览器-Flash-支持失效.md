---
layout: post
title: Adobe Flash Player 升级导致 Kubuntu 下所有浏览器 Flash 支持失效
categories:
- Diandian
tags:
- Linux, 
---
<p>不知道Ubuntu和Debian是怎么的，但是Kubuntu确实是彻底没了Flash支持。刚才找到一个临时解决办法：sudo dophin 到 /opt/chrome/ 新建一个叫plugins的文件夹然后把在Adobe官网下载的开发代号为Square的libflashplayer.so文件复制到这个文件夹里面（1）。之前我看到&nbsp;/opt/chrome/ 下已经有很多后缀为so的文件，和PDF有关，所以就直接发libflashplayer.so放过来，其实这样做是不行的，必须建立一个文件夹。</p>
<p>&nbsp;</p>
<p>（1）Adobe官方下载64位Square：</p>
<p>&nbsp;&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_2_p3_64bit_linux_111710.tar.gz</p>
<p>（**）32位到http://labs.adobe.com/downloads/flashplayer10_square.html选32位下载</p>
<p></p>