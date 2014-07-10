---
layout: post
title: SunPinyin无法安装之分析
categories:
- Diandian
tags:
- Linux, 
---
对于Ubuntu系统，对于Deb包，我们只需要
<a href="http://www.91files.com/?ES8G1UMAGHB9CTSK8NW8" target="_blank">sunpinyin-data-le_1.0~hg20090201-1_all.deb</a>和
<a href="http://www.91files.com/?KTJBXTL5QYGT6HU6L6DY" target="_blank">scim-sunpinyin_1.0~hg20090201-1_i386.deb</a>两个软件包。这两个软件包网上几乎没有下载，我是从6xun中下载的，不过速度极慢，而且文件不全，所以这一套文件完全是我东拼西凑的。因此我将此套包传到网上。
<br />但是，由于如下分析：
<br />dpkg：依赖关系问题使得 scim-sunpinyin 的配置工作不能继续：
<br /> scim-sunpinyin 依赖于 libgtk2.0-0 (&gt;= 2.14.1)；然而：
<br /> 系统中 libgtk2.0-0 的版本为 2.12.9-3ubuntu5。
<br /> scim-sunpinyin 依赖于 libpango1.0-0 (&gt;= 1.21.6)；然而：
<br /> 系统中 libpango1.0-0 的版本为 1.20.5-0ubuntu1。
<br /> dpkg：处理 scim-sunpinyin (--install)时出错：
<br /> 依赖关系问题 - 仍未被配置由于我使用的是LTS（8.04）,我换了9.04的源，但是相应的包虽然版本更新了，但是几乎系统中所有的软件都依赖以上几个软件包，所以这就等于要彻底更新所有的软件，相当于升级到9.04,为了一个输入法，实在不值得。所以我放弃此时的升级，还是高考以后用9.04的Kubuntu吧。