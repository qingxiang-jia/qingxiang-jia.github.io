---
layout: post
title: A Benchmark Flaw
tags:
- Java

---
Would declaring a String variable and then using it run faster or just using a String literal run faster? I had this in mind, and made the following test.

```
public static void main(String[] args) {
    String a = "kNuZbcI4No";
    Path path = Paths.get("10000.txt");

    long start2 = System.currentTimeMillis();
    try (Stream<String> lines = Files.lines(path)) {
      lines.forEach(s -> s.equalsIgnoreCase("5GxtHQS42y"));
    } catch (IOException e) {
      System.out.println(e);
    }
    long end2 = System.currentTimeMillis();

    long start1 = System.currentTimeMillis();
    try (Stream<String> lines = Files.lines(path)) {
      lines.forEach(s -> s.equalsIgnoreCase(a));
    } catch (IOException e) {
      System.out.println(e);
    }
    long end1 = System.currentTimeMillis();

    System.out.println("case variable: " + (end1 - start1) + " ms");
    System.out.println("case literal : " + (end2 - start2) + " ms");
  }
```
The file `10000.txt` contains 10000 random strings. "kNuZbcI4No" is the last one; "5GxtHQS42y" is the second last one.

It turns out using variable is around 6-7 times faster than using literal. This is surprising since I expect the two to be equally fast. Just in case, I switch the order, so this time, "variable block" runs first and then "literal block" runs. This time, literal approach is faster. So, whatever runs second is faster. This is not surprising, since JVM may have done some sort of caching after the first block.

To be safe, I ran both blocks separatly, it turns out both are equally fast.