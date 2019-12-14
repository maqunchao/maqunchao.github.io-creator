---
title: "CSS知识总结"
date: 2019-12-14T00:15:34+08:00
draft: false
---

# CSS知识总结

## 浏览器渲染原理

* 浏览器将获取的HTML文档解析成DOM树。
* 根据CSS，构成层叠样式表模型CSSOM(CSS Object Model),或者说构建css树。
* 将DOM和CSSOM合并为渲染树(rendering tree)。
* 渲染树的每个元素包含的内容都是计算过的，它被称之为布局layout(文档流、盒模型、计算大小和位置)。
* painting绘制(把边框颜色、文字颜色、阴影等画出来)。
* Compose合成(根据层叠关系展示画面)

![](https://raw.githubusercontent.com/maqunchao/maqunchao.github.io-creator/master/image/dom.png)


## CSS 动画的两种做法（transition 和 animation）

### transition 过渡动画
```javascript
transition：属性名 时长 过渡方式 延迟。
transition：left 200ms linear。
还可以用逗号分隔两个不同属性：
transition：left 200ms，top 300ms。
也可以用all来代表所有属性：
transition：all 1s；
过渡方式：
linear | ease(默认) | ease-in | ease-out | ease-in-out | cubic-bezier | step-start | step-end | steps

注意：
并不是所有属性都可以过渡
display：none --> block 就不能过渡
使用visibility:hidden -> visible 或者opacity来过渡,过渡后宽高仍然存在, 需要手动删除样式
```

### animation

```javascript
animation：时长|过渡方式|延迟|次数|方向|填充模式|是否暂停|动画名
时长：1S或者1000ms
过渡方式：同transition取值相同，如：linear
次数：1或者2.5或者infinite
方向：reverse|alternate|alternate-reverse
填充模式：none|forwards|backwards|both
是否暂停：paused|running
```

### CSS盒模型

* centent-box和border-box
内容盒模型的width = contentmaqunchao.github.io-creator
边框盒模型的width = content + padding*2 + border*2
也就是说，一个div，他的内容宽content为100px，padding为10px，border为1px，margin为10px，那么在内容盒模型的解析下，他的width = 100px，也就是content的宽度
而在边框盒模型的解析下，他的width = 100px + 1px*2 + 10px*2 = 122px.
centent-box就是以内容盒模型的方式解析当前盒子，即此时盒子的width = content的宽度
border-box就是以边框盒模型的方式解析盒子，此时width = content + padding*2 + border*2
box-sizing的作用就是规定当前盒子已哪种方式解析当前盒子。(常用border-box)

