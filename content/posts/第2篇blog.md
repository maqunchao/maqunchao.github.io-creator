---
title: "Hugo配合GitHub搭建博客"
date: 2019-11-18T06:15:34+08:00
draft: false
---

# Hugo配合GitHub搭建博客

## 下载hugo 
* 首先安装hugo [地址](https://gohugo.io/)
* 配置环境变量,将存放hugo.exe的文件目录,示例:D:\SoftWare\hugo, 编辑到Path中,点击确定
* 验证hugo是否配置成功, 打开终端,执行hugo version, 成功如下:
```
hugo version
Hugo Static Site Generator v0.59.1-D5DAB232 windows/amd64 BuildDate: 2019-10-31T15:22:43Z
```
## 创建GitHub仓库
* github-->右上角的new repository, 名称:你的github用户名.github.io; (记住仓库名称, 最好用英文)
* 在本地硬盘, 创建一个文件夹, 选中文件夹,执行 
```
hugo new site xxxx(GitHub仓库名称)
```
创建完成后, 本地文件生成一个 xxxx目录, 目录介绍:
创建完成之后的目录介绍：
|- archetypes 存放default.md ,头文件格式
|-content content 目录存放博客文章（.markdown/.md文件）
|-data 存放自定义模板，导入的toml文件（或json、yaml）
|-layouts layouts目录存放网站的网站模板文件
|-static 存放js/css/img 等静态资源
|-config.toml config.toml 是网站的配置文件
* 然后 cd xxxx(目录下) 
* 执行 git init; 初始化本地仓库
* 添加一个默认的主题 命令行执行
```
git submodule add https://github.com/budparr/gohugo-theme-ananke.git themes/ananke
echo 'theme = "ananke"' >> config.toml
```
* 创建可编写博客的markdown文件
```
hugo new posts/my-first-post.md
```
打开my-first-post.md, 如下:
```
title: "Hugo配合GitHub搭建博客"
date: 2019-11-18T06:15:34+08:00
draft: false
```
- draft: true 时，创建的文章hello.md是草稿，Hugo 默认不会将草稿生成静态页面，必须将hello.md文章中的draft: true修改为draft: false；
- 可以直接修改archetypes/default.md配置文件，设置draft: false，关闭草稿功能
* 编写后执行 hugo server -D; 控制台输出
```
hugo server -D

                   | EN
+------------------+----+
  Pages            | 10
  Paginator pages  |  0
  Non-page files   |  0
  Static files     |  3
  Processed images |  0
  Aliases          |  1
  Sitemaps         |  1
  Cleaned          |  0

Total in 11 ms
Watching for changes in /Users/bep/quickstart/{content,data,layouts,static,themes}
Watching for config changes in /Users/bep/quickstart/config.toml
Environment: "development"
Serving pages from memory
Running in Fast Render Mode. For full rebuilds on change: hugo server --disableFastRender
Web Server is available at http://localhost:1313/ (bind address 127.0.0.1)
Press Ctrl+C to stop
```
* 修改 config.toml文件
```
//默认为：
baseURL = "http://example.org/"
languageCode = "en-us"
title = "My New Hugo Site"
//修改为
baseURL = "github发布出去的博客地址"
languageCode = "en-us"
title = "博客名称"
```

*  即开启本地服务,可输入http://localhost:1313/, 进行预览
*  预览后, 执行hugo -D, 输出静态页面,存放在目录下的 public 目录中

## 上传public目录到GitHub

### 将输出的静态博客网页, 提交到本地仓库
1. 在当前目录执行 cd public/
2. 执行 git init
3. 再提交所有文件, git add .
4. git commit -v; 提交到本地仓库
### 关联远程仓库
1. git remote add origin git@github.com:xxx/x.github.io.git
2. git push -u origin master
### 打开GitHub上该仓库的GitHub Pages, 即可浏览该网页

