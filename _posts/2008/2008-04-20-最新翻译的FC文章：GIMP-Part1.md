---
layout: post
title: 最新翻译的FC文章：GIMP-Part1
categories:
- Diandian
tags:
- Linux, 
---
翻译：Lee
<br />翻译状态：100%（完成）
<br />校对：
<br />校对状态：
<br />二校：
<br />二校状态：
<br />正体：
<br />正体状态：
<br />
<br />GIMP-Part1
<p><strong>GIMP</strong> part 1</p>
<p>This series of tutorials, based on GIMP 2.4.2, will not cover every square inch of GIMP, since that would fill a book (and indeed has already filled several), but by the end you will be proficient enough in GIMP to create anything from simple web banners to large posters suitable for professional printing.</p>
<p>这个系列的教程是以GIMP2.4.2为基础的，不会包含HIMP的方方面面，如果全部写出来一整本书都写不完（其实已经填满了好几本书了），但看完了此教程你将会对GIMP足够精通于创建任何简单却很专业的网页元素。<br /></p>
<p>First, let's open GIMP and have a quick look at its layout. Please note that a first load of GIMP may look slightly different from my layout (below). I will briefly discuss the GIMP layout first.</p>
<p>首先，打开GIMP然后看看它的布局。请注意，第一次打开GIMP的时候你看到的布局可能和我的有一些不同。（如下图）我们首先将会简单讨论一下GIMP的布局。</p>
<img src="http://m1.img.srcdd.com/farm4/d/2012/0627/10/4A7A032479CB16B574ED5A107DB5AF5D_B500_900_500_347.JPEG" />
<br />
<p> </p>
<p>On the top left we see the tools and on the bottom left we see the options for the chosen tool (Paintbrush in this case).</p>
<p>在左上角我们看到了工具，在其下面我们可以看到已选择的工具的详细选项（我们这里的选项是刷子工具）Top right are tabs for Layers, Channels and so on and at the bottom right are tabs for Brushes amongst other things.右上角是层标签、通道等等，在右下角我们可以看到刷子工具的标签。 GIMP has a very flexible layout system in that you can drag and drop items from place to place.GIMP有一个非常灵活的界面，你可以从一个地方随意拖拽工具栏另一个地方。 For example, if I want to have my Layers presented on a separate window I can click on the Layers tab (top right, shown below) and drag out to my desktop.比如，如果我想让我的层面板和其它面板分开，我就可以点击层面板标签（右上角，如下图）然后拖出该面板。</p>
<img src="http://m1.img.srcdd.com/farm5/d/2012/0627/10/85C7551396ACA1B9687F9B1025618182_B500_900_325_223.JPEG" />
<p> </p>
<p>If I want to have the Layers display back where it was, I click and drag on the word 'Layers' on the window and drag it back to the top left (below).</p>
<p>如果我想要让层面板回到它原来的位置，我只需要在“层”上面点一下然后拖拽它到左上角。（如下图）</p>
<img src="http://m3.img.srcdd.com/farm5/d/2012/0627/10/95ACC33806DDBBB25742637917712843_B500_900_449_325.JPEG" />
<br />
<p> </p>
<p>You can do this with anything you like so feel free to configure your layout to whatever makes you most comfortable.</p>
<p>你可以随意改变程序的界面，只要你觉得适合你自己。</p>
<p>If, by accident, you close any of your windows and need to get them back, click on File &gt; Dialogs and then the item you want shown, or hidden, for that matter (below).‘</p>
<p>如果你不小心关闭了面板，要想恢复，可以点击“文件 &gt; 对话框”然后选择你想要显示、隐藏的文件。（如下图）</p>
<img src="http://m1.img.srcdd.com/farm5/d/2012/0627/10/283B4B373813985F69C7001813DAD419_B500_900_500_379.JPEG" />
<br />
<p> </p>
<p>Let's create a new image. In the main menu, click File &gt; New. Before we go any further, let me explain what some of these things do.</p>
<p>让我们创建一个新的文件。在主菜单里面，点击 文件 &gt; 新建。在我们继续学习之前，让我解释一下这些选项是用来干什么的。</p>
<img src="http://m3.img.srcdd.com/farm4/d/2012/0627/10/0D1679189A3DB644BB31FEB372EE0D7A_B500_900_392_295.JPEG" />
<br />
<p> </p>
<p>At the top of the window where it says 'Template' is where we can choose from a variety of different pre-configured sizes. Click the drop down menu and choose 'A4'.</p>
<p>在对话框的最上面，有一个“模板”，我们可以用它来简单地选择已经配置好的文件。点击下拉按钮然后选中“A4”。</p>
<p>Below that is 'Image Size'. This is now set to what we've just chosen, A4, so there's no need to alter these values just yet. To the right of the 'Height' value is a measurement type.</p>
<p>下面的”图像尺寸“显示的就是刚刚我们设置的”A4“大小，所以说现在没有必要去设置那些数值了。”高度“的右边是单位。</p>
<p>At the moment, mine is set to millimeters but with a click of the drop down menu I can change it to pixels if I want. Below the width and height are two small boxes.</p>
<p>这时，我的选项是米，但是如果我愿意我可以通过点击下拉菜单把它改变成像素为单位。下面的两个小矩形按钮是图像文件横竖的选择。</p>
<p>Looking closely at the icons on the buttons should help you guess that the one on the left is for portrait (a vertical image) and the other for landscape (a horizontal image).</p>
<p>左边的按钮是让图像竖着放，右边的按钮是让图像横着放。</p>
<p>For the moment, I'll keep it on portrait. A brief summary of your chosen options are to the right of these two buttons. Last on this window is 'Advanced Options'.</p>
<p>这时，我选择竖着放。右边的注释说明了你的选择。（是竖着放还是横着放，多少像素等）Clicking the words 'Advanced Options' reveals more options.点击”高级选项“可以看到更多的选项。</p>
<img src="http://m3.img.srcdd.com/farm5/d/2012/0627/10/B60B250FB731CE5917F67D4D827F887C_B500_900_392_505.JPEG" />
<p> </p>
<p>First we have X and Y Resolution values. These specify how detailed your image will be. This is also known as Dots Per Inch (DPI) and is crucial in printing.</p>
<p>首先我们有X、Y坐标值。这个决定了你的图像显示的位置。这个和每英寸点数（DPI）一样，对于印刷至关重要。</p>
<p>Professional print houses will usually demand at least 200dpi, but mostly 300dpi. Beside the values you can see a small icon which are links in a chain.</p>
<p>专业的印刷厂通常使用200-300dpi的文件。X、Y值的右边有一个铁链标志。</p>
<p>In my image they are linked this means changing the X value will change the Y value automatically, clicking the icon will unlink them and allow different X and Y values.</p>
<p>他们代表，X、Y值的绑定，即你如果改变了X值，那么Y值也会按比例变化。相反，点击铁链标志将取消X、Y的坐标绑定。</p>
<p>If your icon shows the chain links as open then you will want to click it to have them as shown in the image above.</p>
<p>如果你看到”铁链“打开了，你单击就可以把坐标轴显示在编辑的图像上方。</p>
<p>For just a basic test image, change the X or Y value to 100.Next is 'Color Space'.</p>
<p>本教程的图像，选择X=100,Y=100，然后是”颜色空间“。</p>
<p>I only have two options: 'RGB Color' or 'Grayscale' so I am keeping it at 'RGB color'. 'Fill With' lets you choose a starting color for your image.</p>
<p>我只有两个选项：RGB和灰度图。我选择RGB。”默认填充“将让你选择图像起始的背景颜色。</p>
<p>Finally 'Comment' something that will be saved as part of your GIMP file. This could be anything from copyright information to your contact details.</p>
<p>最后的”注释“是你的GIMP文件的一部分。这个可以是关于版权的任何东西。</p>
<p>With my options set, I click OK.在选择了各种选项以后，我点击”确定“。</p>
<img src="http://m2.img.srcdd.com/farm5/d/2012/0627/10/47B31C5BCB7FCC80CB859954E19E7686_B500_900_500_348.JPEG" />
<p> </p>
<p>So now I have a fresh image to work on. But how do you work on an image? We'll get in to that in more detail later but for now I will do a quick run through of some of the more important tools.</p>
<p>现在我面前时一张白纸。但是，怎么在一个白纸上开始工作呢？为此我们将会简单介绍一些很重要的工具。</p>
<img src="http://m3.img.srcdd.com/farm4/d/2012/0627/10/D4D220DD6286973CD9EDC3181DE11A11_B500_900_320_400.PNG" />
<br />
<p> </p>
<p>As you click on each tool the 'Tool Options' (below the tools) will change. Each tool has its own set of options which I won't go in to but play around with these options, that's how you learn more!</p>
<p>你在任何一个工具上点击的时候”工具选项“（在工具下面）将会改变。每一个工具有它自己的选项，我不会一一介绍，那就看你自己的了！</p>
<p><strong>Next month in part two we'll look into color correction and color editing.</strong></p>在下期的续集里面，我们将讨论颜色修正和颜色编辑。