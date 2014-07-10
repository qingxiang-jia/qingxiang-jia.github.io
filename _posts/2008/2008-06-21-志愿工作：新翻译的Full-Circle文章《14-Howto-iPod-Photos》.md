---
layout: post
title: 志愿工作：新翻译的Full Circle文章《14-Howto-iPod Photos》
categories:
- Diandian
tags:
- Linux, 
---
翻译：Lee （贾庆祥）
<br />翻译状态：Done
<br />校对：
<br />校对状态：
<br />二校：
<br />二校状态：
<br />正体：
<br />正体状态：
<br />
<br />IPodPhotos ipod上里的照片
<br />
<p><strong>iPod Photos</strong></p>
<p><strong>ipod里的照片<br /></strong></p>
<p>For several years, various iPod models have supported storing and viewing photos. However, Apple does not support Linux users with its iTunes software. Thankfully, Flavio Gargiulo has come to the rescue with GPixPod.</p>
<p>今年里，有很多型号的ipod已经支持存储和查看照片。然而，苹果并没有提供给Linux用户iTunes软件。幸运的是，Flavio Gargiulo已经开发出GPixPod解决了此问题。</p>
<p>GPixPod (<a href="http://www.gpixpod.org/">http://www.gpixpod.org/</a>) is an elegant tool for managing photos on an iPod, but, I hit a brick wall when I first started using it. <br /></p>
<p>GPixPod(<a href="http://www.gpixpod.org/">http://www.gpixpod.org/</a>)是一个简练的ipod照片管理工具程序，但是呢，我刚开始用的时候遇到了麻烦。</p>
<p>GPixPod is available from the universe repository, and is easy to install using your favorite package manager. After installation, GPixPod is available from the Applications &gt; Graphics menu.</p>
<p>GPixPod就在universe源分类里面，通过你最喜欢的安装管理器可以很容易地安装它。安装以后，GPixPod在程序 &gt; 图像 菜单。</p>
<p>When you first open GPixPod, you will probably be greeted with a slightly daunting dialog (Figure 1) asking for an iPod Photo Database. This database resides on your iPod.</p>
<p>当你一地此打开GPixPod，你大概将会看到一个令人畏缩的对话框并要求你给出一个ipod照片的目录。这个目录在你的ipod里面。</p>
<p>As a confused iPod novice, I canceled this dialog and went in search of GPixPod's configuration in Edit &gt; Preferences.</p>
<p>作为一个ipod新手，我取消了这个对话框然后进入GPixPod在“编辑&gt; 选项”里的设置搜索。</p>
<p>the preferences dialog (Figure 2), I could see that GPixPod was looking for an iPod mounted at /mnt/ipod - which did not exist on my system.</p>
<p>如图二的设置对话框，我可以看到GPixPod 正在/mnt/ipod （在我的系统里并不存在）搜寻一个ipod的挂载点。</p>
<p>Changing the 'iPod mountpoint' to the actual iPod device connected to the computer solved the problem of the missing iPod Photo Database.</p>
<p>改变“ipod挂载点”，真正连上ipod的时候解决了找不到ipod 的照片目录的问题。</p>
<a href="http://fullcirclemagazine.org/docs/uploads/ipodphotos1.jpg" target="_blank"><img alt="http://fullcirclemagazine.org/docs/uploads/ipodphotos1.jpg" src="http://m1.img.srcdd.com/farm3/d/2012/0306/12/DOWNLOADFAILAAAAAAAAAAAAAAAAAAAA_B500_900_200_80.PNG" /></a>
<br />
<strong>Figure 1:</strong> GPixPod will ask for an iPod Photo Database when opened.
<br />图1：GPixPod被打开的时候将会问你ipod的照片目录。
<a href="http://fullcirclemagazine.org/docs/uploads/ipodphotos2.jpg" target="_blank"><img alt="http://fullcirclemagazine.org/docs/uploads/ipodphotos2.jpg" src="http://m1.img.srcdd.com/farm3/d/2012/0306/12/DOWNLOADFAILAAAAAAAAAAAAAAAAAAAA_B500_900_200_80.PNG" /></a>
<br />
<strong>Figure 2:</strong> The GPixPod Preferences showing the incorrect iPod mount point.
<p>After choosing your connected iPod in the Preferences dialog, GPixPod will prompt you to create a Photo Database for storing details about your albums and photos.</p>
<p>图二：GPixPod选项显示了错误的ipod挂载点。</p>
<p>在你在选项对话框中选择了连接ipod之后，GPixPod将会立刻为你存储照片和相册创建目录。</p>
<a href="http://fullcirclemagazine.org/docs/uploads/ipodphotos3.jpg" target="_blank"><img alt="http://fullcirclemagazine.org/docs/uploads/ipodphotos3.jpg" src="http://m1.img.srcdd.com/farm3/d/2012/0306/12/DOWNLOADFAILAAAAAAAAAAAAAAAAAAAA_B500_900_200_80.PNG" /></a>
<br />
<strong>Figure 4:</strong> GPixPod can create your iPod Photo Database.
<p>Once you create the iPod Photo Database, using GPixPod is wonderfully simple. New photo albums can be created using the 'Add Album' button on the main toolbar, and photos can be added from your computer to the iPod using the 'Add Photos' button. The one potential snag here is that the albums and photos are not saved to the iPod until you click the 'Save' button.</p>
<p>图4：GPixPod能够创建你的ipod照片目录。</p>
<p>一旦你创建了ipod照片目录，使用GPixPod将变的很简单。一个潜在的问题是相册和照片都不会保存到ipod上在你点击“保存”按钮的时候。</p>
<a href="http://fullcirclemagazine.org/docs/uploads/ipodphotos4.jpg" target="_blank"><img alt="http://fullcirclemagazine.org/docs/uploads/ipodphotos4.jpg" src="http://m1.img.srcdd.com/farm3/d/2012/0306/12/DOWNLOADFAILAAAAAAAAAAAAAAAAAAAA_B500_900_200_80.PNG" /></a>
<br />
<strong>Figure 6:</strong> GPixPod showing a Full Resolution photo
<p>GPixPod is an essential tool for Ubuntu iPod users, once you overcome the iPod Photo Database hurdle.</p>
<p>图6：GPixPod 正显示一张全分辨率的照片。</p>
<p>对于Ubuntu用户来说GPixPod是一个必不可少的工具在你解决了ipod照片目录问题以后。</p>
<p></p>
<hr />
<p><strong>Additional Screens Unused:</strong></p>
<p><strong>（抱歉，这里翻译不出）<br /></strong></p>
<a href="http://fullcirclemagazine.org/docs/uploads/ipodphotos5.jpg" target="_blank"><img alt="http://fullcirclemagazine.org/docs/uploads/ipodphotos5.jpg" src="http://m1.img.srcdd.com/farm3/d/2012/0306/12/DOWNLOADFAILAAAAAAAAAAAAAAAAAAAA_B500_900_200_80.PNG" /></a>
<br />
<strong>Figure 5:</strong> Don't forget to 'Save' any new albums and photos.
<br />图5:不要忘了“保存”任何新的照片和相册。
<a href="http://fullcirclemagazine.org/docs/uploads/ipodphotos6.jpg" target="_blank"><img alt="http://fullcirclemagazine.org/docs/uploads/ipodphotos6.jpg" src="http://m1.img.srcdd.com/farm3/d/2012/0306/12/DOWNLOADFAILAAAAAAAAAAAAAAAAAAAA_B500_900_200_80.PNG" /></a>
<br />
<strong>Figure 3:</strong> Choosing the real mounted iPod from the Preferences menu.图3：从设置菜单中选择一个正确的挂载点。