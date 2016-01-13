---
layout: post
title: An Infinite GC Problem
tags:
- Garbage Collection 
- Java

---
Recently in work, I encountered an interesting GC (garbage collection) related problem. We have a console like application, when a user logs in, the program loads the corresponding history file so that the user is able to look for "recent commands". However, when the history file is very large (say, 200 MB), this loading process triggers GC. This sounds right because the file is very large, reading it all into the memory will create a memory shortage and thus triggers the GC.

When I first looked at this problem, I am curious why that there is no any trimming. So, I added code to do that. There are so many ways to do that. A trivial but definitely stupid one is to read in all the lines, and count, and remove the lines over the limit. So, to prevent loading in the entire file, I used [LineNumberReader](https://docs.oracle.com/javase/7/docs/api/java/io/LineNumberReader.html), which counts the total number of lines without reading in extra data. After I know how many lines the file has, I can decide whether to truncate the file.

To truncate the file is easy, I used BufferedReader, skipping the first (total - truncate_limit) number of lines, and write the rest of lines back.

When I thought that I was done with the problem, during testing I found no matter what limit I set (> 500), the file would end up having exatly 500 lines. This seems strange. It turns out, we used [JLine](http://jline.sourceforge.net/) to handle the console input, and this library will trim the history file. However, a quick look at is source code, at least in its 1.0 version, it does truncation in the previously mentioned stupid way -- reading in all lines, and count, if too many, remove the lines. This is soure of the GC problem.