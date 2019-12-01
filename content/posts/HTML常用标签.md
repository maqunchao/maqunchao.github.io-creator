---
title: "HTML常用标签"
date: 2019-11-29T13:48:51+08:00
draft: false
---

# HTML常用标签

## a标签包含href, target, download, rel=noopener属性
1. href(hypertext reference)属性:

*   href后面的url,以http/https开头的，则点击a标签后,会链接该url的页面
*   href后是#, 点击后回到页面顶部
```JavaScript
<a href="#">点击回到顶部</a>
```
* 如果href后面是//baidu.com, 浏览器先去http://www.baidu.com寻找, 找不到再去https://www.baidu.com/寻找
```JavaScript
<a href="//qq.com">QQ</a>
```
* href后面可以跟文件路径, 如果我们http-server开启本地服务的方式打开文件, 则会根据本地服务的协议,决定使用http/https打开该文件, <hr> 如果直接双击打开,则使用file://协议打开该文件
* 
* href做伪协议, 
```JavaScript
<a href="javascript:">点击后不会跳转, 无反应</a> 如果javascript:代码,执行该代码
<a href="mailto:邮箱">发邮件</a>
<a href="tel:手机号">打打电话</a>
```
* href来做锚点,跳转到当前页面中某标签的id为xxx的页面元素
```JavaScript
<a href="#xxx">xxx</a>
```
1. target属性
```JavaScript
在新页面打开：<a href="url/相对路径" target="_blank">xxx</a> <hr>
在当前页面打开：<a href="url/相对路径" target="_self">xxx</a><hr>
在父页面打开（有两个页面时）：<a href="url/相对路径" target="_parent">xxx</a><hr>
在最顶层页面打开（有多于两个页面）：<a href="url/相对路径" target="_top">xxx</a>
```
4. download 属性
* 下载页面, 不是所有浏览器都支持
  
## iframe标签
iframe标签用于在一个页面当中嵌套页面,但目前已经很少用了，基本都是在一些旧项目才会看到。
可以a标签进行使用,如下, 点击a标签, 则会在iframe标签内打开指定的url页面
```JavaScript
<iframe name=xxx src="#" frameborder="0"></iframe>

<a target=xxx href="url">abc</a>
```
## table标签
```JavaScript
   <style>
        table{
            width:600px;
            table-layout: auto; 
            // 有auto, fixed两个属性, fixed是适用宽度后. 宽度等分
            border-collapse: collapse;  /* 控制table合并, 消除空间间隙 */
            border-spacing: 0px;
        }
        td,
        th {
          border: 1px solid blue;
        }
    </style>
</head>
<body>
    <table>
        <thead>
            <tr>
                <th></th>
                <th>小红</th>
                <th>小白</th>
                <th>小明</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <th>数学</th>
                <td>213</td>
                <td>123</td>
                <td>150</td>
            </tr>
            <tr>
                <th>语文</th>
                <td>213</td>
                <td>123</td>
                <td>150</td>
            </tr>
            <tr>
                <th>英语</th>
                <td>213</td>
                <td>123</td>
                <td>150</td>
            </tr>
        </tbody>
        <tfoot>
            <tr>
                <th>总分</th>
                <td>565</td>
                <td>577</td>
                <td>585</td>
            </tr>
        </tfoot>
    </table>
</body>
```
![](../../image/
table.png)

## img标签
* 作用:发出get请求, 展示一张图片
1. 属性 alt/height/width/src, src(sourc):图片地址, alt:当图片加载失败, 显示文字提升我们
2. 事件: onload:图片加载成功时. onerror:图片加载失败时调用,使用该函数可加载缺省图片
3. 设置img的样式: max-width:100%, 是图片变成响应式
   
## form标签
* 属性
1. action: 控制请求那个页面, 请求页面的地址
2. method: 使用POST/GET 进行请求
3. autocomplete: 自动填充(包含input标签进行使用时,), on开启, off关闭, 
4. target: 提交到那个页面, _blank(新页面)

* 在form里, 必须有一个type=submit的标签,如果写个button,不写type,button默认submit
* 如果form里, input的type=submit, 则也可当做提交, 与button的区别是:input不能有其他内容, <hr>但是button可以设置其他标签内容
* form里面的input标签需要设置name

## input标签
* checkbox与radio属性,(checkbox通常用于多选，radio通常用于单选)
* checkbox也可做单选,设置name相同即可实现单选效果, 如果设置name=hobby,则是一组的多选
* 当type=file时,是选中文件, 如果加上multiple,则是多文件选中上传.

## textarea标签(多行输入)
* 设置style: resize:none; 这样可以设置宽高, 不让该标签拉伸
  
##  select + option  做下拉选项
* option里面value是实际值, 包含内容是显示值
```JavaScript
<select name="setop">
      <option value="">-</option>

      <option value="1">第一组</option>

      <option value="2">第二组</option>

      <option value="3" disable>第三组</option>

      <option value="4" selected>第四组</option>
    </select>
```
  

