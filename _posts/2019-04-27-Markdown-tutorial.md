---
title: Markdown Tutorial
layout: post
categories: Language
tags: Markdown
excerpt: markdown basic grammar tutorial
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

- ##### 引用<br> 
> Quote写法：\> Quote <br> 

- 粗体<br> 
**Bold**写法：\**Bold**<br> 

- 斜体<br> 
*Italic*写法：\*Italic*<br> 

- 链接<br> 
[Link](https://yansicing.github.io/)写法：\[Link](https://yansicing.github.io/)

- 参考<br> 
References [Markdown Extra][2]：References \[Markdown Extra\]\[2\]

- 横线<br> 
下划线_或星号*三个以上<br> 

- 换行<br> 
\<br> 或 \<\br> <br>

- 单行文字空格<br> 
单行文字首个空格会被忽略，如果想要显示首行空格，把输入法的半角改成全角输入 <br>

- 单行文字显示<br> 
    单行文本显示，在首行加入俩个tab键或四个空格 <br>
	
- 多行文字显示<br> 
    多行文本显示，在首行加入俩个tab键或四个空格 <br>
    多行文本显示，在首行加入俩个tab键或四个空格 <br>
    多行文本显示，在首行加入俩个tab键或四个空格 <br>

- 文字高亮显示<br> 
将强调部分用 \`  ` 包围起来，达到文字`高亮显示`<br>
注意不是单引号，而是Tab上方，数字1左边按键（英文输入法）<br>

- 普通分级
1. 数字后面加一个点，再加一个空格
2. 数字后面加一个点，再加一个空格
3. 数字后面加一个点，再加一个空格

- 圆点符分级<br> 
* 一级圆点号 ： `星号* + 空格` 
	* 二级圆点号：`tab + 星号* + 空格`
		* 三级圆点号：`2个tab + 星号* + 空格` 
	
- 缩进符分级
n个\> <br>

> 层次一  
>> 层次二
>>> 层次三  
>>>> 层次四
>>>>> 层次五

- 标题<br> 
\# 一级标题<br>

# 一级标题
## 二级标题
### 三级标题
#### 四级标题
##### 五级标题
###### 六级标题

- 插入图片<br> 
网络上的图片格式：\!\[](图片URL)<br> 
[]方括号里可以加描述，描述不会对图像显示造成任何改动 <br>
![yansicing](http://yansicing.net3v.net/head.jpg) <br>

 在URL后面，加双引号包围的字符串，显示悬停 <br>
![yansicing](http://yansicing.net3v.net/head.jpg " head portrait ")<br>

 GitHub仓库里的图片，格式：\!\[](图片URL)<br>
 图片URL格式：` https://github.com/ 用户名 / 项目名 / raw / 分支名 / 存放图片的文件夹 / 该文件夹下的图片`<br>
![github picture](https://github.com/yansicing/yansicing.github.io/raw/master/assets/res/logo.png)<br>

 图片加超链接格式：文字链接格式 + 插入图片格式 即：
\[\!\[](图片URL) \](图片的超链接)<br>
[![yansicing](http://yansicing.net3v.net/head.jpg)](https://yansicing.github.io)<br>

 文字悬停，第一种方式 <br>
[![yansicing](http://yansicing.net3v.net/head.jpg "yansicing")](https://yansicing.github.io)<br>

 文字悬停，第二种方式 <br>
[![yansicing](http://yansicing.net3v.net/head.jpg)](http://https://yansicing.github.io "yansicing.github.io")<br>

- 插入代码片段<br>
在代码起始行用三个\`标记，Tab键上面的键。语法高亮要在 \`之后加上编程语言（忽略大小写）<br>

 普通写法
```
Drawable drawable = ivSystem.getDrawable();//java
```

 高亮写法
``` java
Drawable drawable = ivSystem.getDrawable();//java
```

- 锚点<br>
其实每一个标题都是一个锚点（移动到某个位置）<br>
比如 [回到顶部](### 目录)

- 表格<br>
每个格短横线-要大于一个<br>

|表头1  |表头2  |
|--- |---|
|内容1  |内容2  |
|内容1  |内容2  |

- 字体<br>
|语法    |效果  |
|---|---|
| \*斜体1* | *斜体1* |
| \_斜体2_ | _斜体2_|
| \*\*粗体1** | **粗体1** |
| \_\_粗体2__ | __粗体2__|
|  \~\~删除线~~ | ~~删除线~~ |
| \*\*\*斜粗体1*** | ***斜粗体1*** |
| \_\_\_斜粗体2___ | ___斜粗体2___ |
| \*\*\*\~\~斜粗体删除线1~~*** | ***~~斜粗体删除线1~~*** |
| \~\~\*\*\*斜粗体删除线2***~~ | ~~***斜粗体删除线2***~~ |

- ##### [Above reference][7]

#### 表格 <span id="1.2">

- **Markdown　Extra**表格语法

项目     | 价格
--- | ---
Computer | $1600
Phone    | $12

- 冒号定义左右对齐：

| 项目      |    价格 | 数量  |
| :--- | ---:| :--: |
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
[7]: https://blog.csdn.net/rain_9155/article/details/82731732