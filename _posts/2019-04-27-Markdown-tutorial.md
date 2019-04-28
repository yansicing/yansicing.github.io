---
title: Markdown Tutorial
layout: post
categories: Language
tags: Markdown
excerpt: markdown grammar simple tutorial
---
## Markdown简明语法教程 <span id="home">
---
	
### 目录

* **[特性介绍](#1)**
	* **[常用](#1.1)**
	* **[表格](#1.2)**
	* **[图片](#1.3)**
	* **[列表](#1.4)**
	* **[代码](#1.5)**
	* **[脚注](#1.6)**
	* **[公式](#1.7)**
* **[浏览器兼容](#2)**
* **[常用Markdown编辑器推荐](#3)**
* **[参考文献](#4)**
* 
---

### 特性介绍<span id="1">
	
- **Markdown和扩展Markdown简洁的语法**
- **代码块高亮**
- **图片链接和图片上传**
- ***LaTex*数学公式**
- **离线写博客**
- **导入导出Markdown文件**

---

#### 常用 <span id="1.1">

- > 引用 Quote —— <a href="https://zh.wikipedia.org/wiki/Markdown" target="_blank"> [ 维基百科 ]
- **粗体 Bold**
- *斜体 Italic*
- [链接 Link](https://yansicing.github.io/)
- 参考 References [Markdown Extra][2]

#### 表格 <span id="1.2">

- **Markdown　Extra**表格语法

项目     | 价格
-------- | ---
Computer | $1600
Phone    | $12

- 冒号定义左右对齐：

| 项目      |    价格 | 数量  |
| :-------- | --------:| :--: |
| Computer  | 1600 元 |  5   |
| Phone     |   12 元 |  12  |
| Pipe      |    1 元 | 234  |

#### 图片 <span id="1.3">
- 格式一：简单
 
``` markdown
 ![head](http://yansicing.net3v.net/head.jpg)
```

- 格式二：(可设置图片尺寸)

``` html
<img src="http://yansicing.net3v.net/head.jpg" alt="download-failed" width="100px"  height="100px">
```

#### 列表 <span id="1.4">

**Markdown　Extra**列表语法：
项目１
项目２
:   定义 A
:   定义 B

项目３
:   定义 C
:   定义 D

	> 定义D内容

#### 代码 <span id="1.5">

- Python:

``` python
@requires_authorization
def somefunc(param1='', param2=0):
    '''A docstring'''
    if param1 > param2: # interesting yansicing~
        print 'Greater'
    return (param2 - param1 + 1) or None
class SomeClass:
    pass
>>> message = '''interpreter
... prompt'''
```

- C:

``` c

#include <stdio.h>
	int main()
	{
		printf("Hello yansicing~");
	}

```

#### 脚注  <span id="1.6">

- 生成一个脚注[^footnote]
  [^footnote]: 这里是 **脚注** 的 *内容*
  
#### 公式  <span id="1.7">
使用MathJax渲染 *LaTex* 数学公式，详见[math.stackexchange.com][1]，更多LaTex语法参考[mathjax-basic-tutorial-and-quick-reference][3]

 - 行内公式：$\Gamma(n) = (n-1)!\quad\forall n\in\mathbb N$
 - 块级公式：\$$ \$$ $$	x = \dfrac{-b \pm \sqrt{b^2 - 4ac}}{2a} $$

### 浏览器 <span id="2">

 1. 本编辑器对Chrome浏览器支持最完整,建议使用较新版本Chrome
 2. IE9以下不支持
 3. IE9，10，11存在以下问题
    1. 不支持离线功能
    1. IE9不支持文件导入导出
    1. IE10不支持拖拽文件导入

### 常用Markdown编辑器推荐 <span id="3">

1. **Markdownpad**：[官网](http://markdownpad.com/)
（貌似专业版需要收取一定dollars$，需要序列号自行baidu。）
2. **Markpad**：[官网](http://markpad.fluid.impa.br/)
（推荐使用，Microsoft Store也有，完全免费，支持及时效果浏览。）
3. **CSDN博客编辑器**：CSDN内置编辑器
4. **Harropad**: [官网](http://pad.haroopress.com/user.html)
5. **Retext**: 简单强大的文本编辑器，可控制输出格式pdf, html等，仅支持Linux（推荐）[下载](https://github.com/retext-project/retext)

#### 参考文献 <span id="4">
- [knightyun](https://knightyun.github.io)

------

#### **返回[顶部](#home)**

---------

[1]: http://math.stackexchange.com/
[2]: https://github.com/jmcmanus/pagedown-extra "Pagedown Extra"
[3]: http://meta.math.stackexchange.com/questions/5020/mathjax-basic-tutorial-and-quick-reference
[4]: http://bramp.github.io/js-sequence-diagrams/
[5]: http://adrai.github.io/flowchart.js/
[6]: https://github.com/benweet/stackedit