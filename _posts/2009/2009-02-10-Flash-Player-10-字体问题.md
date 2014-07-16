---
layout: post
title: Flash Player 10 字体问题
categories:
- Diandian
tags:
- Linux

---
症状：显示中文的字体为方框
<br />解决方法：修改/etc/fonts/conf.d/49-sansserif.conf文件，把里面定义的涉及“sans-serif”的字体换成包含中文的字体。
<br />具体步骤：
<br />&lt;match target=&quot;pattern&quot;&gt;
<br />−
<br />&lt;test qual=&quot;all&quot; name=&quot;family&quot; compare=&quot;not_eq&quot;&gt;
<br />&lt;string&gt;sans-serif&lt;/string&gt;
<br />&lt;/test&gt;
<br />−
<br />&lt;test qual=&quot;all&quot; name=&quot;family&quot; compare=&quot;not_eq&quot;&gt;
<br />&lt;string&gt;serif&lt;/string&gt;
<br />&lt;/test&gt;
<br />−
<br />&lt;test qual=&quot;all&quot; name=&quot;family&quot; compare=&quot;not_eq&quot;&gt;
<br />&lt;string&gt;monospace&lt;/string&gt;
<br />&lt;/test&gt;
<br />−
<br />&lt;edit name=&quot;family&quot; mode=&quot;append_last&quot;&gt;
<br />&lt;string&gt;文泉驿正黑&lt;/string&gt;
<br />&lt;/edit&gt;
<br />&lt;/match&gt;
<br />
<br />把最下面的改成文泉驿正黑（如果装了的话）就行了