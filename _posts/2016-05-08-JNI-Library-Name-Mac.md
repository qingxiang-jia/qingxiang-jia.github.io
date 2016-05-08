---
layout: post
title: JNI Library Name on Mac
tags:
- C++
- Java
- JNI

---
If you try a hello world example for JNI programming, it may tell you that you can just use `System.loadLibrary(hello);` to load a native library (may be C++, may be C, or some other language). Specifically, on Windows, this "hello" means "hello.dll"; on Linux or Unix, it means "hello.so". I guess Mac is just one of the Unix members, so I have a shared library compiled and named "hello.so".

But I got "UnsatisfiedLinkError". I double checked my `java.library.path`, and there was no problem. Since Mac actually uses `*.dylib` for shared library, I then renamed my library into "hello.dylib", but it didn't work either -- I still got the same error. Then I realized the library, was originally named `libhello.dylib`, I followed the tutorial so I renamed it. Maybe that's the correct name? I tried, and that worked!