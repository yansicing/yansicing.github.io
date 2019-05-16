---
title: Git with Visual Studio Code
layout: post
categories: Git
tags: Git GitHub VS
excerpt: Visual Studio Code using Git

---
#### Visual Studio Code与Git <span id="home">
---

__持续更新（updating···）__

---
VS Code 集成了Git功能，并支持基本的git命令，这使得我们能够在开发过程方便的提交和获取代码

使用版本控制系统，要以**纯文本**方式编写文件。因为文本是有编码的，比如中文有常用的GBK编码，日文有Shift_JIS编码，如果没有历史遗留问题，强烈建议使用标准的`UTF-8`编码，所有语言使用同一种编码，既没有冲突，又被所有平台所支持。

不要使用Windows自带的记事本编辑任何文本文件。原因是Microsoft开发记事本的团队在保存UTF-8编码的文件时，他们在每个文件开头添加了0xefbbbf（十六进制）的字符，会遇到很多不可思议的问题。比如，网页第一行可能会显示一个“?”，明明正确的程序一编译就报语法错误，等等。建议使用Notepad++代替记事本，记得把Notepad++的默认编码设置为UTF-8 without BOM即可

#### 操作步骤

##### 1. Git存储库初始化
* 新建工作目录`yang`
* 将`yang`添加到Resource manager中
* View-Command palette-Git:Initialize Repository

##### 2. 暂存和提交
* 显示Git输出：Show Git Output
* 点击+号暂存所有更改
* 提交到本地代码库

##### 3. 提交代码到Github

* Github新建代码仓库`yang`
* 在`yang`中打开Git Bash
* `git config --global user.name "Your Name"`
* `git config --global user.email "email@example.com"`
* 查看用户名：`git config user.name`
* 查看邮箱：`git config user.email`

* 初始化本地仓库：`git init`
* 暂存已更改文件：`git add . `
* 提交所有文件：`git commit -m “备注信息”`












* ```git remote add origin https://github.com/yansicing/yang.git```
* ```git pull origin master```
* 代码合并后，最新的工作目录下面多了`LICENSE`和`README.md`
* 发布分支：Publish Branch
##### 4. 克隆远程仓库
* 工作目录克隆远程代码仓库，然后用Visual Studio Code 打开

#### Git命令






---

> 待完善（To be added~）

---


##### 参考文献 <span id="4">
- [fylstudio-Windows10和Visual Studio Code环境中配置使用Git和GitHub](https://blog.csdn.net/fylstudio/article/details/79106331)
- [捷风-git终端合并代码的简单使用](https://www.jianshu.com/p/220c6846badf)
- [廖雪峰的官方网站-Git教程](https://www.liaoxuefeng.com/wiki/896043488029600/896827951938304)
- [Pro Git book](https://git-scm.com/book/zh/v2)
- [Git的详细使用教程——三部曲](https://blog.csdn.net/oman001/article/details/80208632)









---
##### **返回[顶部](#home)**