---
title: Playwright
date: 2022-03-28 16:44:00
---

# <mark>Playwright</mark>

---

# 官网

[Playwright](https://playwright.dev/)

# 安装

安装Playwright库本体

```bash
pip install playwright
```

安装浏览器驱动文件

```bash
python -m playwright install
```

包括Chromium、Firefox、WebKit等浏览器的驱动文件

# 使用方法

Playwright支持自动录制，且非常智能。录制完成后会自动生成代码文件，然后根据需要修改代码文件。

## 录制

### 录制帮助

```bash
python -m playwright codegen --help
```

### 常用录制命令

```bash
python -m playwright codegen --target python -o "out.py" -b chromium http://xxx.xxx
```

其中：

- `-target`：规定生成脚本的语言，可以选择JS和Python，缺省为Python
- `-b`：规定浏览器驱动
- `-o`：将录制脚本保存到一个文件

关闭浏览器即可结束录制。

## 手动处理代码文件

### 创建浏览器

```python
browser = playwright.chromium.launch(headless=False)
```

### 创建context

```python
context = browser.new_context()
```

### 创建标签页面

```python
page = context.new_page()
```

### 添加Cookies

```python
with sync_playwright() as p:
    browser_type = p.chromium
    browser = browser_type.launch(headless=False)
    context = browser.newContext()
    context.addCookies(cookies=[{'name': 'xx','value':'xx','path':'xx','domain':'xx'},
                                {'name': 'xx','value':'xx','path':'xx','domain':'xx'}]
    page1 = context.newPage()
```

### 跳转网址

```python
page.goto('xxx')
```

### 网页定位

一般自动录制的就可以，也可以手动选择。

```python
page.locator("input[name=\"password\"]")
page.locator("label span")
page.locator("canvas")
```

### 点击

```python
page.locator("input[name=\"password\"]").click()
```

```python
page.locator("canvas").click(position={"x":849,"y":446})
```

### 填充字符

```python
page.locator("input[name=\"password\"]").fill("abcdefg")
```

### 关闭页面、content和浏览器

```python
page.close()
context.close()
browser.close()
```