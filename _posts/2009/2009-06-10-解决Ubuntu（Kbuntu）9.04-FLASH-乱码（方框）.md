---
layout: post
title: 解决Ubuntu（Kbuntu）9.04 FLASH 乱码（方框）
categories:
- Diandian
tags:
- Linux, 
---
网上流行的方法（有效、正确） 若所播放的flash里有字体乱码（显示为方块），那么按如下方法解决： 1 在终端里输入sudo gedit /etc/fonts/conf.d/49-sansserif.conf然后回车 2 将倒数第四行 sans-serif 改为 文泉驿正黑 保存即可，重启firefox，flash乱码解决了。 建议：将“文泉驿正黑”换成“微软雅黑”如果你有这个字体的话。不是我不支持开源字体，微软雅黑本身技术很经典，字形也好看，没必要追求纯开源。 注：在Kubuntu中“gedit”换成“kate”