---
title: Nginx
date: 2022-03-27 19:13:00
---

# <mark>Nginx</mark>

# 官网

[Nginx](http://nginx.org/)

[Nginx官方使用方法](http://nginx.org/en/docs/windows.html)

# 安装

解压即可使用。

# FIRST COMMAND

查看版本：

```bash
nginx -v
```

# 配置

Nginx使用他运行的目录作为配置中相对路径的前缀。

## 配置文件

在当前工作目录/conf/nginx.conf文件。

### 监听端口

http/server/listen可以设置监听端口。

### 负载均衡

http/server/location/proxy_pass可以设置请求转发地址池。

weight是各服务器被访问到的权重，数值越大访问到的几率越高。

### 静态资源

/hhtp/server/location/

例如：

```apacheconf
index index.html
```

错误日志文件

在当前工作目录/logs/error.log文件。

# 使用方法

进入工作目录。

## 开启Nginx服务

```bash
start nginx
```

开启后访问以下网址进行测试：

```url
http://localhost
```

## 查看Nginx服务

```bash
tasklist /fi "imagename eq nginx.exe"
```

其中有两个Nginx进程，一个是主进程，一个是工作进程。

## 关闭Nginx服务

```bash
nginx -s stop
nginx -s quit
```

前者是快速停止，可能并不保存相关信息；后者是完整有序的停止，并保存相关信息。

## 使用新配置重载

```bash
nginx -s reload
```

## 重写log文件

```bash
nginx -s reopen
```

# 缺陷

## 多副本启动

尽管可以启动多个副本，但是只有一个可以工作。

## UDP相关

不支持UDP代理。