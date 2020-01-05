---
title: "JS函数的执行时机"
date: 2020-01-05T00:15:34+08:00
draft: false
---

# JS函数的执行时机

## 1. 解释为什么下面代码为打印6个6
```JavaScript
let i = 0
for(i = 0; i<6; i++){
  setTimeout(()=>{
    console.log(i)
  },0)
}
```
* 首先在for循环外用let 声明变量i = 0, 开始执行for循环, 此时会先执行for循环,同时设置了6次setTimeout函数(相当于定了6个闹钟);
* setTimeout()会过一会执行, 然后跳过setTimeout(); 然后执行完for循环后, 此时已经执行了6次i++, i的值已经变成了6;
*  然后马上执行setTimeout函数,所以6次的setTimeout中的函数每次都会打印i的值是6;
* 同时类似于下面的函数也是打印6次6
```JavaScript
for(var i = 0; i<6; i++){
  setTimeout(()=>{
    console.log(i)
  },0)
```
* 因为 变量i是var命令声明的, 在全局范围都有效,全局只有一个变量i。每一次循环，变量i的值都会发生改变,6次for循环执行完, i也变成6了, 然后马上执行setTimeout函数,所以6次的setTimeout中的函数每次都会打印i的值是6;

##  setTimeout运行机制
* javascript提供定时执行代码的功能，叫做定时器（timer），主要由setTimeout()和setInterval()这两个函数来完成。它们向任务队列添加定时任务;
* setTimeout和setInterval的运行机制是，将指定的代码移出本次执行，等到下一轮Event Loop(事件循环)时，再检查是否到了指定时间。如果到了，就执行对应的代码；如果不到，就等到再下一轮Event Loop时重新判断。这意味着，setTimeout指定的代码，必须等到本次执行的所有代码都执行完，才会执行
* 每一轮Event Loop时，都会将“任务队列”中需要执行的任务，一次执行完。setTimeout和setInterval都是把任务添加到“任务队列”的尾部。因 此，它们实际上要等到当前脚本的所有同步任务执行完，然后再等到本次Event Loop的“任务队列”的所有任务执行完，才会开始执行。由于前面的任务到底需要多少时间执行完，是不确定的，所以没有办法保证，setTimeout和 setInterval指定的任务，一定会按照预定时间执行
```JavaScript
setTimeout(someTask,100);
add();
```
上面的setTimeout，指定100毫秒以后运行一个任务。但是，如果后面立即运行的任务（当前脚本的同步任务））非常耗时，过了100毫秒还无法结束，那么被推迟运行的someTask就只有等着，等到前面的add运行结束，才轮到它执行。
``` JavaScript
setTimeout(function () {
    func1();
}, 0)
func2();
```
* setTimeout的作用是将代码推迟到指定时间执行，如果指定时间为0，即setTimeout(f,0),那么会立刻执行吗？ 答案是不会,setTimeout运行机制说过，必须要等到当前脚本的同步任务和“任务队列”中已有的事 件，全部处理完以后，才会执行setTimeout指定的任务。也就是说，setTimeout的真正作用是，在“任务队列”的现有事件的后面再添加一个 事件，规定在指定时间执行某段代码。setTimeout添加的事件，会在下一次Event Loop执行。所以即使第二个参数设置为0, 其作用也是尽可能早的执行指定任务.

  
## 2. 写出让上面代码打印 0、1、2、3、4、5 的方法
```JavaScript
for(let i = 0; i<6; i++){
  setTimeout(()=>{
    console.log(i)
  },0)
}
```
* 这样就会打印0,1,2,3,4,5; 因为for循环中用let声明i, 当前的i只在本轮循环有效,所以每次循环的i,其实都是一个新的变量,本轮循环结束后,并且JavaScript引擎内部会记住上一轮循环的的值,然后初始化本轮的变量i时,就在上一轮循环的基础上进行计算.
  
## 除了使用 for let 配合，还有什么其他方法可以打印出 0、1、2、3、4、5，

1. 使用立即执行函数
* 立即执行函数会形成一个单独的作用域，我们可以封装一些临时变量或者局部变量，避免污染全局变量
* 下面用立即执行函数，给每个setTimeout创建一个独立的作用域,i的值从0到6，当i=6时已经不满足i<6,所以对应六个立即执行函数,这6个立即执行函数的m分别是0,1,2,3,4,5 所以能正常输入

```JavaScript
for(var i = 0; i<6; i++){
  !function(m){
    setTimeout(()=>{
        console.log(m)
    },0)
  }(i)
  //把实参i赋值给形参m
}
```
2. 使用setTimeout的第3个参数
* 第三个参数就是给setTimeout第一个函数的参数, 由于每次传入的参数是从for循环里面取到的值(参数i实时传给定时器)，所以会依次输出0~5。
```JavaScript
for(var i=0;i<6;i++){
    setTimeout(function(j){
        console.log(j);
    },i*1000,i);
}
```





















































