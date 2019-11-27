---
title: "HTML入门笔记"
date: 2019-11-27T06:15:34+08:00
draft: false
---

## 历史简介

* 1990年, Tim Berners-Lee发明了HTML, 自己编写了一个浏览器和服务器, 然后通过自己的浏览器访问了自己写的服务器.

## HTML 起手式

```html
<!DOCTYPE html>  <!-- 文档类型 -->
<html lang="zh-CN"> <!-- html标签, 改成中文 -->
  <head>
    <meta charset="UTF-8" />
    <!-- 文件的字符编码 -->
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <!-- 禁用缩放, 兼容手机 -->
    <meta http-equiv="X-UA-Compatible" content="ie=edge" />
    <!-- 告诉IE浏览器, 使用最新版本 -->
    <title>Document</title>
    <!-- 网页标题 -->
  </head>
  <body></body>
</html>
```

## 常用的表示章节的标签


* h1 ~ h6, 标题标签， 呈现六种不同级别的标题，由大到小
* section, 章节标签， 表示一个包含在HTML文档中的独立部分
* article,  表示文章
* p，段落标签 
* header， 头部
* footer，脚部，一般表示根元素的页脚
* main， 主要内容
* aside， 旁支内容
* div， 块级元素, 可用来划分
  
## 全局属性

1. class, 给标签分类或者标记
```javascript
 <div  class="middle open ">  
   
</div>
```

2. contenteditable, 表示元素是否被用户编辑
   
 ```javascript
 <div  contenteditable="true">  
</div>
```
3. hiddle, 可用来隐藏页面元素
4. id, 定义了全局唯一的标识, 但页面如果存在多个一样的id,并不会报错, 谨慎使用
5. style, 行内样式优先级高于外联css样式, 低于JS设置
6. tabindex, 页面元素是否聚焦, 可使用Tab键进行选择切换
```
tabindex = 正值  表示该元素可以被选择，从小到大的进行选取。
tabindex = 0    表示该该元素最后被选取。
tabindex = 负值  表示该元素不会被选取，一般赋值'-1'.
```
7. title, 表示咨询信息文本，和它术语的属性相关，可显示完整的内容，可与省略号一起使用, 见下面示例。

```css
.bg{
    white-space: nowrap; <!-- 内容不换行 -->
    overflow: hidden;   <!-- 超出内容部分隐藏 -->
    text-overflow: ellipsis;<!-- 用省略号结尾 -->
}
```
## 常用内容标签
1. ol + li 有序列表 ordered list
2. ul + li 无序列表 unordered list
3. dl + dt + dd   一个词一个描述内容
4. pre, 在 HTML 中，多个空格回车或者tab，都只会缩进成一个空格, pre会保留内容的回车和空格
5. code，使内容字体等宽
6. hr， 水平分割线， 一般使用于页面评论
7. br， 使内容换行（break）
8. a， 超链接标签，配合target= "_blank",点击链接后在新窗口打开，否则在当前窗口打开
9. em, 强调,侧重于语气
10. strong, 强调重要, 侧重于内容
11. quote, 内联的引用
12. blockquote, 块级的引用