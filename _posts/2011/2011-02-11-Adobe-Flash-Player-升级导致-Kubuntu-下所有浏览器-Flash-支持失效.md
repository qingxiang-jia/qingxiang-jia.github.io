---
layout: post
title: Adobe Flash Player 升级导致 Kubuntu 下所有浏览器 Flash 支持失效
categories:
- Diandian
tags:
- Linux, 
---
不知道Ubuntu和Debian是怎么的，但是Kubuntu确实是彻底没了Flash支持。刚才找到一个临时解决办法：sudo dophin 到 /opt/chrome/ 新建一个叫plugins的文件夹然后把在Adobe官网下载的开发代号为Square的libflashplayer.so文件复制到这个文件夹里面（1）。之前我看到 /opt/chrome/ 下已经有很多后缀为so的文件，和PDF有关，所以就直接发libflashplayer.so放过来，其实这样做是不行的，必须建立一个文件夹。   （1）Adobe官方下载64位Square：           http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10\\\_2\\\_p3\\\_64bit\\\_linux\\\_111710.tar.gz （\\\*\\\*）32位到http://labs.adobe.com/downloads/flashplayer10\\\_square.html选32位下载