---
layout: post
title: 我和荷笠联合翻译的文章：CProgramming-Part2 (C)
categories:
- Diandian
tags:
- Linux

---
<p>一个第二循环在47搭配57行；这是一个for循环，一下是它的语法：</p>
<p>for(init_variable;condition;update_variable)<br />{<br />&nbsp;&nbsp;&nbsp;&nbsp; statements;<br />}<br /></p>
<br />
<p>Here, there are three parts: first a loop variable is initialized to a value (typically 0 but in our example to 1), next there is a condition which is checked on every iteration and the for loop will continue as long as this condition is true, and finally the variable is updated -- this is typically a 'i++' (i++ is shorthand for i=i+1). It is good style to use while loops when you don't know the number of iterations up front, and a for loop when you do know, and thus do not need to modify the loop variable in the loop body.</p>
<p>The language has two other constructs which are not present in the example. First there is the:<br /></p>
<p>这 里有三个部分：第一，一个循环变量被初始化的值（通常是0但是在我们的例子里是1），接着，这里有一个被每个循环核实的条件，并且for循环会继续执行下 去直到这个条件为真，最终得到的变量是更新的——这通常是“i++”（i++是i=i+1的缩写）。当你不想知道循环的前面的数字时，使用while循环 是一个很好的作风，当你已经知道了一个for循环时，因此就不需修改循环体中的循环变量。<br />C语言还有两个别的结构，并没有显示在例子中。第一个是：</p>
<p><br /></p>
<p>do<br />{<br />&nbsp;&nbsp;&nbsp;&nbsp; statements;<br />}while(condition);<br /><br />do<br />{<br />&nbsp;&nbsp;语句；<br />}while（表达式）；<br /></p>
<br />
<p>Here, the statements will be executed as long as condition is true, which is almost the same as the while loop. The difference is that the body will be executed at least once. While loops are, however, more common than do...while.</p>
<p>A more popular format which has been omitted here is the switch...case construct:</p>
<p>在这里，只要条件为真，statements语句将会被执行，效果和while循环一样。所不同的是它循环体会被执行至少一次。然而，while循环比do……while循环更普遍。</p>
<p>一个更受欢迎的，在那里已被省略了的是switch…cases语句：<br /></p>
<p>switch(variable)<br />{<br />case 1:<br />&nbsp;&nbsp;&nbsp;&nbsp; statements1;<br />&nbsp;&nbsp;&nbsp;&nbsp; break;<br />case 4:<br />case 2:<br />&nbsp;&nbsp;&nbsp;&nbsp; statements2;<br />&nbsp;&nbsp;&nbsp;&nbsp; break;<br />default:<br />&nbsp;&nbsp;&nbsp;&nbsp; statements3;<br />}<br /></p>
<p>This is a very compact form of writing if..else if...else if...else statements. A switch is passed a variable on which the decision will be based, and this is followed by a list of case keywords succeeded by all cases which need handling (here, one will typically use enum with a limited range). Statements can be terminated with break, otherwise execution would fall through (which also has its uses) and continue the statements of the next case (if variable equals 4, statements2 will be executed). And finally there is a default which stands for 'all other cases'.<br /></p>
<p>if..else if...else if...else语句是一个非常简洁的编写形式。一个switch函数是通过一个变量……（这里，大家通常会使用一个范围有限的枚举）。语句必须能用break终止，否则将不能执行（这同样也有用途）并且继续下一个case语句（如果变量为4，语句2会被执行。）最后这里用一个default关键字表示“所有其他的case”</p>
<p>One final note: it is possible to jump out of if..else, while, for, do..while and switch...case blocks by using the 'break;' statement. And it is possible to proceed with the next iteration (of a loop) by using the 'continue;' statement.</p>
<p>一个最后的提示：break语句可以用于跳出 if…else，while，for，do…while和switch…case。也可以用continue语句继续执行下一个循环（在这个循环中）。<br /></p>
<p>Exercises</p>
<p>&middot; Rewrite the for loop in the main() function so it becomes a while loop</p>
<p>&middot; Rewrite the if...else if..else structure in the isPrime() function to a switch...case structure</p>
<p>&middot; Rewrite the ternary (condition)?value1:value2 to an if..else structure</p>
<p>&middot; Rewrite the if...else in the main() function to make use of the ternary operator</p>
<p>&middot; Replace the isPrime() function by an isOdd() function which returns 1 when a given integer is odd.</p>
<p>&middot; Design and write a small application which prints out the n Fibonacci sequence, where n should be easily modifiable.</p>
<br />