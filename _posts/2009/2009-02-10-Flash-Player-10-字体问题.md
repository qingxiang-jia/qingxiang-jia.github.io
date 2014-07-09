---
layout: post
title: Flash Player 10 字体问题
categories:
- Diandian
tags:
- Linux, 
---
症状：显示中文的字体为方框 解决方法：修改/etc/fonts/conf.d/49-sansserif.conf文件，把里面定义的涉及“sans-serif”的字体换成包含中文的字体。 具体步骤：  − sans-serif − serif − monospace − 文泉驿正黑把最下面的改成文泉驿正黑（如果装了的话）就行了