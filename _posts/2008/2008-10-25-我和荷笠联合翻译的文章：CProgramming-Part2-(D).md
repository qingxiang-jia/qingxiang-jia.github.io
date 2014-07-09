---
layout: post
title: 我和荷笠联合翻译的文章：CProgramming-Part2 (D)
categories:
- Diandian
tags:
- Linux, 
---
练习 重写循环中的main主函数，使之成为一个while循环 将isPrime（）函数中的if…else if…else语句重写为switch…case语句 将ternary (condition)?value1:value2三目运算重写为if…else语句 将主函数中的if…else改用三目运算符 将isPrime函数替换为一个isOdd函数，使程序在得到一个整数是奇数时返回第一步 设计并编写一个小的应用程序，实现输出第n位斐波那契数列（），n为易变的 01. \\\#include  02. \\\#define VERSION   "1.0"            03. 04. /\\\* 05. \\\* Runs a prime check on a given integer, return 06. \\\* 1 when the integer is a prime number, 0 otherwise 07. \\\*/ 08. int isPrime(int prime) 09. \\\{ 10.     int count=2; 11. 12.     // Catch two special cases 13.     if(prime==1) 14.     \\\{ 15.         return 0; 16.     \\\} 17.     else if(prime==2) 18.     \\\{ 19.         return 1; 20.     \\\} 21.     else 22.     \\\{ 23.         while(prime%count!=0 && count\\\*count<=prime) 24.         \\\{ 25.             count++; 26.         \\\} 27.         return (prime%count==0)?0:1; 28.     \\\} 29. \\\} 30. Listing 1: flow\\\_control.c part one 31. /\\\* 32.   \\\* Print version information 33.   \\\*/ 34. void printVersion() 35. \\\{ 36.      printf("Primality checker version %s\\\\n", VERSION); 37.      printf("Compiled on %s %s\\\\n", \\\_\\\_DATE\\\_\\\_, \\\_\\\_TIME\\\_\\\_); 38. \\\} 39. 40. int main() 41. \\\{ 42.     int i=1; 43.     const int max\\\_prime=2500; 44. 45.     printVersion(); 46. 47.     for(i=1;i