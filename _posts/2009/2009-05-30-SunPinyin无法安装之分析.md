---
layout: post
title: SunPinyin无法安装之分析
categories:
- Diandian
tags:
- Linux, 
---
对于Ubuntu系统，对于Deb包，我们只需要\[sunpinyin-data-le\\\_1.0~hg20090201-1\\\_all.deb\]\[sunpinyin-data-le\_1.0\_hg20090201-1\_all.deb\]和\[scim-sunpinyin\\\_1.0~hg20090201-1\\\_i386.deb\]\[scim-sunpinyin\_1.0\_hg20090201-1\_i386.deb\]两个软件包。这两个软件包网上几乎没有下载，我是从6xun中下载的，不过速度极慢，而且文件不全，所以这一套文件完全是我东拼西凑的。因此我将此套包传到网上。 但是，由于如下分析： dpkg：依赖关系问题使得 scim-sunpinyin 的配置工作不能继续： scim-sunpinyin 依赖于 libgtk2.0-0 (>= 2.14.1)；然而： 系统中 libgtk2.0-0 的版本为 2.12.9-3ubuntu5。 scim-sunpinyin 依赖于 libpango1.0-0 (>= 1.21.6)；然而： 系统中 libpango1.0-0 的版本为 1.20.5-0ubuntu1。 dpkg：处理 scim-sunpinyin (--install)时出错： 依赖关系问题 - 仍未被配置由于我使用的是LTS（8.04）,我换了9.04的源，但是相应的包虽然版本更新了，但是几乎系统中所有的软件都依赖以上几个软件包，所以这就等于要彻底更新所有的软件，相当于升级到9.04,为了一个输入法，实在不值得。所以我放弃此时的升级，还是高考以后用9.04的Kubuntu吧。 \[sunpinyin-data-le\_1.0\_hg20090201-1\_all.deb\]: http://www.91files.com/?ES8G1UMAGHB9CTSK8NW8 \[scim-sunpinyin\_1.0\_hg20090201-1\_i386.deb\]: http://www.91files.com/?KTJBXTL5QYGT6HU6L6DY