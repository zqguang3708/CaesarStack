---
title: GitBook
date: 2022年3月27日18点33分

---

# <mark>GitBook</mark>

> 有本地版和网页版两种。推荐使用本地版。
> 
> > 网页版：[GitBook网页版](htps://www.gitbook.com/)
> > 
> > 以下介绍本地版。

# 本地版基本信息

> 本地版依赖node.js，且由于GitBook长期未维护，只能使用v10.21.0及之前的版本。所以推荐使用nvm管理node.js。

[GitBook in npm](https://www.npmjs.com/)

在npm官网搜索GitBook，里面会有具体的说明。

# 安装

```bash
npm install gitbook-cli -g
```

# FIRST COMMAND

查看版本：

```bash
gitbook -v
```

# 初始化项目

在项目文件夹中，

```bash
gitbook init
```

> 会自动创建README.md和SUMMARY.md，分别是介绍文档和目录文档。

> 和Github类似，GitBook也提供了忽略文件，GitBook会依次读取.gitignore，.bookignore，.ignore文件。一个文件一行，可以用通配符。

```bash
npm init
```

由于后面使用npm管理，所以需要进行npm初始化。
如果你真的不使用npm管理，也可以不进行这一步。

会自动创建npm项目的配置文件package.json。

# 初始化配置和插件

## 初始化配置文件

在项目文件夹根目录新建book.js或book.json文件，作为配置文件。

> 注意，json文件内不能含有注释。如果想加注释，只能用js文件。

常用配置如下，以book.json为例：

```json
{
    "title": "书名",
    "description": "描述",
    "isbn": "图书编号",
    "author": "作者",
    "lang": "zh-cn",
    "plugins": ["search-pro", "code", "expandable-chapters", "back-to-top-button", "theme-lou"],
    "pluginsConfig": {
        "fontSettings": {
            "theme": "sepia",
            "family": "sans",
            "size": 4
        }
    },
    "vairables": {}
}
```

## 插件相关

### 查找插件

插件同样在[npm官网](https://www.npmjs.com/)搜索，关键词为`gitbook-plugin-`。

### 常用插件列举

增强搜索：

```bash
npm install gitbook-plugin-search-pro
```

代码框：

```bash
npm install gitbook-plugin-code
```

菜单折叠：

```bash
npm install gitbook-plugin-expandable-chapters
```

返回顶部：

```bash
npm install gitbook-plugin-back-to-top-button
```

自定义主题插件：

```bash
npm install gitbook-plugin-theme-主题名
```

### 插件安装方法

在配置文件中（book.js或book.json）下的plugins的list里添加插件名。只添加`gitbook-plugin-`后面的即可，如：

```textile
search-pro
code
expandable-chapters
back-to-top-button
theme-主题名
theme-aleen42
theme-beauty
theme-comscore
theme-cuav
theme-door
theme-gestalt-yl
theme-het-ycy
theme-jolie
theme-lou
theme-seers
```

# Write Book

## 章节配置说明

SUMMARY.md是链接列表文件，名字是章节的名字，链接指向章节文件的路径。

子章节可以直接内嵌。

例如：

```md
# 概要

- [第一章](part1/README.md)
  - [1.1 第一节](part1/writing.md)
  - [1.2 第二节](part1/gitbook.md)
- [第二章](part2/README.md)
  - [2.1 第一节](part2/feedback_please.md)
  - [2.2 第二节](part2/better_tools.md)
```

## 具体内容

直接写相关md文件即可。

# 启动项目

有两种方法进行：

- 使用gitbook管理运行

- 使用npm管理运行

有两种启动方式：

- 打包成HTML静态文件并启动Web服务

- 仅打包成HTML静态文件

这两种方法都可以任意选择启动方式

## GitBook管理运行

### 打包并启动Web服务

在项目文件夹中，

```bash
gitbook serve
```

在项目根目录会生成_book_文件夹，里面是HTML静态文件。同时可以通过以下网址访问。

```url
http://localhost:4000
```

### 仅打包成HTML静态文件

在项目文件夹中，

```bash
gitbook build
```

同上，只不过不会开启Web服务。

## npm管理运行

修改package.json文件，在scripts下面添加：

```json
"scripts":{
    "serve": "gitbook serve",
    "build": "gitbook build"
}
```

然后通过以下命令运行：

```bash
npm run serve
npm run build
```

使用效果同上。

# 高阶操作

## Nginx配置文件参考

```json
server {
    listen       8065;
    server_name  你的服务器IP;

    location / {
        charset utf-8;
        root  /electronic-book-demo/build/;
        index  index.html index.htm;
    }
}
server {
    listen       80;
    server_name  demo.域名.com;

    location / {
        charset utf-8;
        root  /electronic-book-demo/build/;
        index  index.html index.htm;
    }
}
```