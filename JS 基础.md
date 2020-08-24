JS 基础

1. 只有函数有返回值

2. console.log(3) 的返回值：undefined

3. return 后面不可以加回车

4. 表达式1？表示2：表达式3   --->一般用来简化if（表达式1）{ 表达式2} else{表达式3}

5. 真A&&B：短路路径 ，只有A为真，才看B

6. A=A||B :   B保底值，  只有A为A才是A,否则为B

7. 浮点数不可靠：

   - 以下代码死循环

   ```
   var a =0.1;
   while (a!=1) {
   	console.log(a)
   	a=a+0.1
   }
   ```

8. setTimeout(fn) :  fn会改变，所以过一会的值，是等fn内存上的值被操作之后的 值

9. label语法：标签语句 { foo:1 } 是一个标签：foo标签，值=1，不是一个对象 ：A={foo:1} 