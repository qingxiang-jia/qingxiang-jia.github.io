---
layout: post
title: 五步搞定在Google Code上使用Git
categories:
- Diandian
tags:
- Linux
- 网络
- 计算机技术
- Google
- Python

---
<p>网上有很多教程，但是很多都没有结合国情，那就是我们用GoAgent配合Git使用Google Code的代码托管。</p>
<p>第零步：没安装git的安装git，我用Mint，所以是sudo apt-get install git<br /></p>
<p>第一步：到你的代码的根目录，打开终端，输入命令：git init （初始化）</p>
<p>第二步：把这个初始化了的代码仓库加入到你的git：git add . （注意，是空格再句点）</p>
<p>第三步：给我们的软件仓库取个名字：git commit -m &quot;lee-lemmatizer&quot;</p>
<p>第四步：退出来，在home目录下建立一个文件名为：.netrc的文件。把 <a href="https://code.google.com/hosting/settings">https://code.google.com/hosting/settings</a> 上的登录名和密码复制粘贴到文件中，形如： <span>machine code.google.com login ybjqx3340@gmail.com password sdkGJ3fh2fs2adf</span> 注意，最好修改一下文件权限，只让你自己可以看见这个文件的内容，因为密码是明文。</p>
<p>第五步：重新在代码根目录打开终端，输入：git push https://code.google.com/p/lee-lemmatizer/ master 这时你会看到输出告诉你正在上传，一会儿就搞定。</p>
<p>好，如果你在墙内，在安装git后，别忘记在终端输入：<span>git config --global http.proxy &quot;127.0.0.1:8087&quot; 注意你自己的端口号。</span><br /></p>