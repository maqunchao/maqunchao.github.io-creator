---
title: "浅析URL"
date: 2019-12-15T00:15:34+08:00
draft: false
---

# 浅析URL

## url包含部分

* 以下为例子
```
https://baike.baidu.com/item/CSS/5457?fr=aladdin#7
```
1. 传输协议：http，https
2. 域名：baike.baidu.com
3. 端口: http 大部分默认80, https默认443
4. 路径: /item/CSS/5457
5. 查询参数: ?fr=aladdin
6. 锚点: #7
7. ![](https://raw.githubusercontent.com/maqunchao/maqunchao.github.io-creator/master/image/url.jpg)

* 一共有65535个端口（基本够用）
* 要提供HTTP服务最好用80端口
* 要提供HTTPS服务最好用443端口
* 要提供FTP服务最好用21端口
* [端口对应的服务列表] (https://zh.wikipedia.org/wiki/TCP/UDP%E7%AB%AF%E5%8F%A3%E5%88%97%E8%A1%A8)
* 0-1023号端口是留给系统用的，只有拥有了管理员权限之后才能使用，但一般不建议使用
* 一个端口如果被占用，就只能用另一个端口,总之IP和端口缺一不可，IP定位一台设备，端口定位一个设备的服务


## DNS作用, nslookup 命令怎么用
1.DNS：域名系统
过程：当你输入一个网址，你的chrome浏览器会向电信提供的DNS服务器询问这个网址对应的IP
电信会回答一个IP
然后chrome才会想对应IP的80/443端口发送请求
请求内容是查看这个网址的网页

* nslookup可查询IP地址, 命令行输入 nslookup + 域名
```javascript
λ nslookup baidu.com
服务器:  UnKnown
Address:  fe80::1

非权威应答:
名称:    baidu.com
Addresses:  220.181.38.148
          39.156.69.79
```

## IP 的作用是什么，ping 命令怎么用

* IP：internet protocol
* IP主要约定两件事：一是如何定位一台设备；二是如何封装数据报文跟其他设备交流

* ping是一个十分强大的TCP/IP工具。它的作用主要为：
* 用来检测网络的连通情况和分析网络速度；
* 根据域名得到服务器IP；
* 根据ping返回的TTL值来判断对方所使用的操作系统及数据包经过路由器数量。
  
``` javascript
λ ping baidu.com

正在 Ping baidu.com [220.181.38.148] 具有 32 字节的数据:
来自 220.181.38.148 的回复: 字节=32 时间=27ms TTL=53
来自 220.181.38.148 的回复: 字节=32 时间=27ms TTL=53
来自 220.181.38.148 的回复: 字节=32 时间=27ms TTL=53
来自 220.181.38.148 的回复: 字节=32 时间=26ms TTL=53

220.181.38.148 的 Ping 统计信息:
    数据包: 已发送 = 4，已接收 = 4，丢失 = 0 (0% 丢失)，
往返行程的估计时间(以毫秒为单位):
    最短 = 26ms，最长 = 27ms，平均 = 26ms
```

## 域名是什么，分别哪几类域名?

1.  域名: 对IP的一个别称
* 一个域名可以对应不同的IP，这个叫做均衡负载，防止一台机器扛不住。
* 一个IP可以对应不同的域名，这个叫做共享主机，没有钱的开发者一般共享主机
2. 域名分顶级域名，二级域名和三级域名, 就像github.io，把子域名，用户名.github.io免费给用户使用一样，
* .com：指commerce，用于商业性的机构或公司; 
* .net：指internet用于从事Internet相关的网络服务的机构或公司
* .org：指organize，用于非盈利的组织、团体
* .gov.cn：指government，用于政府部门
* .cn/.xx: 由两个字母组成的国家代码，如中国为.CN，日本为.JP，英国为.UK等等
* .info：指information，最新的顶级域名，适用于提供信息服务的公司
* .cc：指commercialcompany，是继.COM和.NET之后的第三大顶级域名，最适用于商业公司


