---
layout: post
title: 用VMware模拟Linux，上网问题解决方案
categories:
- Diandian
tags:
- Linux

---
很多时候用VM虚拟机装Kubuntu等的时候并不能顺利地上网，这里我找到了几个方法和分别适应的情况：
<br />
<p>第一种情况：<br />主机使用PPPOE拨号上网</p>
<p>方法一：NAT方式</p>
<p>1、先关闭虚拟机中的操作系统，回到虚拟机主界面<br />双击主界面右上方的的“Ethernet”，弹出“Network Adapter”对话框，选择“NAT”</p>
<p>2、启动虚拟机操作系统，设置IP为动态获取，即通过DHCP获得。</p>
<p>此时虚拟机中的操作系统用的是主机的IP，主机能够上网，那么虚拟机也能。</p>
<p>方法二：Host-only方式</p>
<p>1、先关闭虚拟机中的操作系统，回到虚拟机主界面<br />双击主界面右上方的的“Ethernet”，弹出“Network Adapter”对话框，选择“Host－only”</p>
<p>2、右击拨号上网的连接，打开PPPOE连接属性，选择“高级”，选择“允许其它网络用户通过此计算机的INTERNET连接来连接”<br />在“家庭网络”下拉框中，选择“VMware Network Adapter VMnet1”<br />VMware Network Adapter VMnet1虚拟网卡的IP会自动变为192.168.0.1<br />此时ping 192.168.0.1 能通即可。</p>
<p>3、进入vmware中，启动linux操作系统<br />用netconfig命令<br />将IP，设为192.168.0.2 （与虚拟网卡在同一网段）<br />网关为192.168.0.1 即VMware Network Adapter VMnet1虚拟网卡的IP地址<br />DNS设置为ISP的DNS，如61.147.37.1</p>
<p>4、重启网络：<br />#service network restart</p>
<p>此时，只要主机拨号上网后，虚拟机的系统就可以上网，且不用再拨号</p>
<p>方法三：Bridge方式</p>
<p>这种方式，虚拟机最接近一台真实的机器</p>
<p>1、先关闭虚拟机中的操作系统，回到虚拟机主界面<br />双击主界面右上方的的“Ethernet”，弹出“Network Adapter”对话框，选择“Bridge”</p>
<p>2、宿主机中安装sygate或wingate之类的代理服务器</p>
<p>3、设置虚拟机的代理服务器为宿主机的IP即可</p>
<p>第二种情况：<br />在单位局域网内</p>
<p>“Ethernet”要选择“Bridge”方式<br />使用这种方式时，虚拟机跟一台真实的机器一样，此时IP设置为局域网中另一个可用IP即可<br />网关：局域网网关服务器的地址（或路由器的地址）<br />DNS:设置为ISP的DNS服务器地址</p>