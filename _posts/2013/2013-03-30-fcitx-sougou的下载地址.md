---
layout: post
title: fcitx-sougou的下载地址
categories:
- Diandian
tags:
- Linux, 计算机技术, 网络, 
---
<p>国内这点事儿就是麻烦，刚刚fcitx-sougou的包放出来，deepin就撤下了。原因貌似是搜狗只同意deepin把这个拼音用在deepin的系统上，所以其他所有Linux发行版都无缘。好吧，既然如此不讲道理，我也无话可说了。其实闭源根本不是问题，有很多闭源软件，比如Skype啊这些，的确是不能看源码，但是没有说只提供给特定的系统用啊（而且本身都是通用的，是人为的不发包）。为了解决这种悲剧的状况，我觉得只能黑吃黑。有这么一个东西叫dpkg-repack，就是用来打包已经安装了的程序。比如，前天我装了fcitx-sougou，但是很快源里就没有这个包了，而我已经清除了下载缓存，这种况下就用dpkg-repack。</p>
<p>以下的下载链接是我用dpkg-repack提取的fcitx-sougou的包，注意因为我用的是64位系统，所以提取出来的包都是64位的:</p>
<pre config="brush:html;toolbar:false;">fcitx_4.2.6.1-2deepin2_all.deb
fcitx-bin_4.2.6.1-2deepin2_amd64.deb
fcitx-config-common_0.4.5.1-1deepin_all.deb
fcitx-config-gtk_0.4.5.1-1deepin_amd64.deb
fcitx-data_4.2.6.1-2deepin2_all.deb
fcitx-frontend-all_4.2.6.1-2deepin2_all.deb
fcitx-frontend-gtk2_4.2.6.1-2deepin2_amd64.deb
fcitx-frontend-gtk3_4.2.6.1-2deepin2_amd64.deb
fcitx-frontend-qt4_4.2.6.1-2deepin2_amd64.deb
fcitx-libs_4.2.6.1-2deepin2_amd64.deb
fcitx-module-dbus_4.2.6.1-2deepin2_amd64.deb
fcitx-module-kimpanel_4.2.6.1-2deepin2_amd64.deb
fcitx-module-lua_4.2.6.1-2deepin2_amd64.deb
fcitx-modules_4.2.6.1-2deepin2_amd64.deb
fcitx-module-x11_4.2.6.1-2deepin2_amd64.deb
fcitx-skin-sogou_0.0.2_all.deb
fcitx-sogoupinyin_0.0.0-2_amd64.deb
fcitx-ui-classic_4.2.6.1-2deepin2_amd64.deb</pre>
<p>顺便说一下，因为华为网盘总是要求在下载文件的时候安装一个他们的插件，我决定不再用华为网盘了（其实不装插件完全可以绕开下载，搞不清楚这些插件又在搜集什么信息），现在用百度网盘。</p>
<p>下载地址：<a href="http://pan.baidu.com/share/link?shareid=355489&amp;uk=2285208125" target="_blank">http://pan.baidu.com/share/link?shareid=355489&amp;uk=2285208125</a></p>