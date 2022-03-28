---
title: Node.js
date: 2022-03-27 19:32:00
---

# <mark>Node.js</mark>

---

# 说明

相关的有三个软件：

- Node.js本体
  
  - [Node.js官网](https://nodejs.org/)

- npm
  
  - Node.js包管理器，会随本体自动安装
  
  - [npm官网](https://www.npmjs.com/)

- nvm
  
  - Node.js版本管理器，需要自行安装
  
  - [nvm in Github](https://github.com/nvm-sh/nvm)
  
  - [nvm for Windows](https://github.com/coreybutler/nvm-windows)

# 安装

有两种安装思路：

- 利用nvm安装

- 手动安装

推荐使用nvm安装，因为有的包只能使用相应版本的Node.js。

## 利用nvm安装

1. 直接安装nvm。

2. 查看已安装的版本
   
   ```bash
   nvm list
   ```

3. 查看所有可以安装的版本
   
   ```bash
   nvm list available
   ```

4. 安装指定版本（同时包括Node.js本体和npm）
   
   ```bash
   nvm install 14.0.0
   ```

5. 查看当前版本
   
   ```bash
   nvm current
   ```

6. 切换当前版本
   
   ```bash
   nvm use 14.0.0
   ```

## 手动安装

下载对应版本直接安装。

# FIRST COMMAND

```bash
node -v
npm -v
node -h
```

# 使用方法

## 初始化环境

进入项目文件夹

```bash
npm init
```

## 查看安装的插件

```bash
npm list
```

## 查找插件

在[npm官网](http://www.npmjs.com/)搜索需要的包，里面有具体的使用说明。

## 安装插件

```bash
npm install xxx
npm i xxx
```

## 运行插件

```bash
npm run
npm run xxx
```