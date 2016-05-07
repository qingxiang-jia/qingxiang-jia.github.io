---
layout: post
title: Static Variable Linking Error
tags:
- C++

---
I was working on a side project. It's in C++. Given that I haven't done much in C++, I treat it as an opportunity to learn C++ as the project progresses. I was stuck on a problem for several days. Here is the problem. I have a class variable (named cache) but it's static. When compile, it keeps telling me: 
> Undefined symbols for architecture x86_64:
  "H264_Decoder::cache", referenced from:
      H264_Decoder::H264_Decoder(void (*)(AVFrame*, AVPacket*, void*), void*) in H264_Decoder.cpp.o
      H264_Decoder::~H264_Decoder() in H264_Decoder.cpp.o
      H264_Decoder::init_ws_server() in H264_Decoder.cpp.o
      
But clearly I have defined it just like other variables. I thought it was the problem of the build tool (Please excuse me, I am new to C++.). I am using CMake as it's the only supported build tool for CLion; I am using CLion as it's the only good cross-platform C++ IDE. To prove this, I spent some time to learn meson, a new build tool. Indeed, meson is great. But that's another story. So I learned meson, and wrote meson.build for my project. I then got the exact the same error -- so, it must not be the problem of the build tool.

What's special about this variable. Well, it's static, all other variables are not. That's probably why. A quick search gives me this [link](http://stackoverflow.com/questions/9282354/static-variable-link-error). Turns out, in C++, if a class variable is static, it should be declared differently. You can find the details in the link.