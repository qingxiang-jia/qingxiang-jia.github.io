---
layout: post
title: Ubuntu——ADSL上网
categories:
- Diandian
tags:
- Linux, 
---
话说我刚刚安装好了UBUNTU,就想着刚快联网，结果发现UBUNTU相关设置里面没有提供ADSL的联网选项，于是查了一下。网上的方法都很简单，所谓的pppoeconf在终端中，然后会弹出很多的设置，建议认真看看，不要跟着别人一路YES，稍有英文基础都可以看懂。(如果最后选了开机自动连接网络，一出现桌面就已经连好网了，看似废话，这一点不知道比WINDOWS方便多少！) 提醒你一点，我之前一直配置不好，就是在一个输入ADSL用户名的地方，默认是username我以为是一个项目的名称，结果直接在后面输入我的账号，当然结果是很惨的。所以，一定要删除username以后在输入用户名。 关闭连接：sudo poff； 打开连接：sudo pon “plog”或“ifconfig ppp0” 查看网络状态