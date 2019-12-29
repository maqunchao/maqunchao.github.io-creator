---
title: "JS对象基本语法"
date: 2019-12-29T00:15:34+08:00
draft: false
---

# JS对象基本语法

## 声明对象的两种语法
```
let obj = {'name':'mark', 'age':26}
let obj1 = new Object({'name':'mark', 'gender':'man'})
```
* 键名是字符串, 不是标识符, 可以包含任意字符
* 键名的引号可省略, 省略后只能写标识符
* 键名的引号省略后, 任然是字符串

```
let obj = {
    1:'a',
    2.6:'b',
    1e2:'c',
    .234:true,
    0XFF:true
}
//属性名都会自动变成字符串
Object.keys(obj)
//得到所以key, ["1", "100", "255", "0.234", "0.26" ]
```
## 查看属性两种方法与变量做属性名

* 中括号语法: obj['key']
* 点语法: obj.key,  key认为是字符串
* 优先使用中括号语法

### 使用变量做属性名

```
let p1 = 'name'
let obj = {p1:'mark'};  属性名是 'p1';
let obj1 = {[p1]:'frank'}; 属性名是 'name';
```
* 不加[]的属性名会自动变成字符串
* 加了[]则会当成变量求值
* 值如果不是字符串, 则会自动变成字符串

```
let list = ['name', 'age', 'gender'];
let person= {name:'mark', age:18, gender:'man'};
for(let i = 0; i<list.length; i++){
        
    //console.log(person[list[i]]); 正常运行
    
    //点语法后面的 obj.key ,  key就是字符串"key";
    //下面代码会直接报错, 点语法 直接当成key是 "list[i]"处理
    // console.log( person.list[i]相当于 person["list[i]"]) ;
    
}

```

## 删除对象的属性

* delete obj.xxx 或者 delete obj['xxx']
即可删除 obj的xxx属性
* 判断不含属性名
```
 'xxx' in obj === false
```
* 含有属性名, 但是值为undefined
```
 'xxx' in obj && obj.xxx === undefined
```
* obj.xxx === undefined, 不能判断 'xxx'是否为obj的属性, 因为obj.xxx的值可能就是undefined
  
## 查看对象的属性

* 查看自身的所以属性
```
    Object.keys(obj); 
// 打印结果是一个数组, 包含了obj的自身属性
```
* 查看自身+共有属性
```
console.dir(obj)
或者用Object.keys打印obj.__proto__
```
* 判断一个属性是自身的还是共有的
```
obj.hasOwnProperty('xxx')
```

## 修改或者增加对象的属性

### 修改
* 直接赋值
```
let obj = {name:'mark'};  //name是字符串
obj.name = 'mark';
obj['name'] = 'mark';

//下面因为name是变量, 不确定值, 会报错
obj[name]

obj.key等价于 obj['key'],  可参考变量做属性名的例子

```
* 批量赋值
```
 Object.assign(obj, {age:18, gender:'man'});
```

### 修改或者增加共有属性

#### 无法通过自身修改或增加共有属性
* let obj = {}, obj2 ={}// 共有toString
* obj.toString = 'xxx' 只会在改obj自身的属性
* obj2.toString 还在原型上, 未改变

#### 强制修改或者增加原型上的属性

* obj.__proto__.toString = 'xxx'; //不推荐
* Object.prototype.toString = 'xxx'
* 一般不要修改原型


#### 修改隐藏属性

* 不推荐使用
```
let obj = {name:'mark'}
let obj1 = {name:'jack'}

let common = {apple:'iPhone'}
obj.__proto__ = common
obj1.__proto__ = common
```
* 推荐使用 Object.create
```
var obj = {name:'mark'};
var obj2 = new Object({name:'kack'});

obj.__proto__ == obj2.__proto__
true
var obj = Object.create({name:'jack'});
obj.__proto__ == obj2.__proto__
false
obj.__proto__.__proto__ == obj2.__proto__
true
```
### 'name' in obj和obj.hasOwnProperty('name') 的区别

```
'toString' in obj
//不管自身属性和共有属性, 只要包含就是true
// true
obj.hasOwnProperty('toString')
//判断一个属性是自身的还是共有的, 自身的true
//false
```

## 原型就是对象, 包含了共有属性