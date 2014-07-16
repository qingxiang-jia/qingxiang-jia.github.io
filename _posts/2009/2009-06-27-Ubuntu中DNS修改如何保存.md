---
layout: post
title: Ubuntu中DNS修改如何保存
categories:
- Diandian
tags:
- Linux

---
修改（sudo）/etx/resolv.conf中的nameserver后面的IP地址为你想要的即可。
<br />这样做以后即时生效，但是不能保存。
<br />所以还需要（sudo）/etc/ppp/peers中的provider里，在userpeerdns前加“＃”，即把它注释掉。