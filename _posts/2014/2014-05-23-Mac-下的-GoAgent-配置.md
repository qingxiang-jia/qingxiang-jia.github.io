---
layout: post
title: Mac 下的 GoAgent 配置
categories:
- Diandian
tags:
- 计算机技术, 网络, 
---
<ol class="edui-filter-decimal">
 <li><p>按照 GoAgent 的配置要求把该做的都做好。</p></li>
 <li><p>用 pip 安装 pycrypto。这里有几个坑：</p></li>
 <ol class="edui-filter-lower-alpha">
  <li><p>网上说用 wget，可是 mac 下默认没有，为这个去装个 wget 没必要。直接下载文件就好了嘛。<a href="https://bootstrap.pypa.io/get-pip.py">https://bootstrap.pypa.io/get-pip.py</a></p></li>
  <li><p>下载了 pip 以后，安装 pip： sudo python get-pip.py （没 sudo 的话没权限）</p></li>
  <li><p>装好 pip 以后，用 pip 装 pycrypto。注意是 pycrypto，之前搜到用人乱指点说用 crypto，也能装上，但这俩不是一个东西。命令：sudo pip install pycrypto</p></li>
 </ol>
 <li><p>把 GoAgent 的证书加到 KeyChain 里。进去找到 login 这个板块，找到 GoAgent，双击打开，看到 Trust，扩展开，在 When using this certificate 选 Always Trust。</p></li>
</ol>