---
title: Git General Tutorial
layout: post
categories: Git
tags: Git 
excerpt: Git with Visual Studio Code

---
#### Git使用教程 <span id="home">
---

__持续更新（updating···）__

---
#### Git工作流程

![git-flowchart](https://github.com/yansicing/yansicing.github.io/raw/master/assets/gitpage_picture/git-flowchart.png)

#### Git命令

|**常用** |**命令**|
|---|---|
|添加到暂存区| git add|
|提交到版本库| git commit|
|提交到远程库 | git push|
|**辅助**	|**命令**|
|初始化仓库|	git init|
|克隆代码	|git clone|
|比较差异	|git diff|
|查看状态|	git status|
|查看日志|	git log|
|检出代码	|git checkout|
|重置代码|	git reset|
|恢复进度	|git stash|
|里程碑	|git tag|
|回滚操作	|git revert|
|获取（不合并）	|git fetch|
|合并操作	|git merge|
|获取并合并(fetch+merge)	|git pull|
|rebase命令（可以处理冲突和合并提交）	|git rebase|

---
#### 本地仓库-Git Bash操作
* 安装Git
* 打开`Git Bash`配置用户名和邮箱：
> `git config --global user.name "Your Name"`<br>
> `git config --global user.email "email@example.com"`
* 查看用户名和邮箱：
> `git config user.name`<br>
> `git config user.email`

* Github新建代码仓库`yang`
> `mkdir yang`
* 初始化本地仓库
> `git init`
* Git提交文件到版本库
> 暂存已更改文件：`git add . `<br>
> 提交所有文件：`git commit -m "备注信息"`
* 查看文件提交及修改状态
> `git status`
* 查看`readme.txt`修改的内容
> `git diff readme.txt`
* 显示从最近到最远的修改日志
> `git log`<br>
> `git log --pretty=oneline `

* 撤销修改
> 1.版本回退：<br>
> `git reset --hard HEAD^`<br>
> `git reset --hard HEAD^^`<br>
> `git reset --hard HEAD~100 `
> 2.回退到特定版本：<br>
> `git reflog`<br>
> `git reset --hard 版本号`
> 3.丢弃（撤销）工作区文件`readme.txt`的修改：<br>
> `git checkout -- readme.txt`

* 删除文件
> `rm readme.txt`<br>
> `git commit -a`

----
#### 远程仓库-提交代码到Github

* 创建SSH Key
> `ssh-keygen -t rsa –C "youremail@example.com"`<br>
> `登录Github---Settings---SSH and GPG Keys---New SSH Key---Title---Key---粘贴id_rsa.pub文件内容---Add SSH Key`

* 测试连接：`git -T git@github.com`

##### 1. 先有本地库，后有远程库
* 在Github上创建远程仓库：`yang`（空）
* 将已有的本地仓库`yang`（非空）与之关联
> `git init`<br>
> `git add .`<br>
> `git commit -m "备注信息"`<br>
> `git remote add origin git@github.com:yansicing/yang.git`<br>
> `git push -u origin master`<br>
> `git pull origin master --allow-unrelated-histories`<br>
* 提交：`git push origin master`
* 拉取：`git pull origin master`

##### 2. 克隆远程库到本地
* 在Github上创建远程仓库：`yang`（非空）
* 克隆远程库到本地
> `git clone git@github.com:yansicing/yang.git`<br>

---
#### Visual Studio Code操作步骤
VS Code 集成了Git功能，并支持基本的git命令，这使得我们能够在开发过程方便的提交和获取代码

使用版本控制系统，要以**纯文本**方式编写文件。因为文本是有编码的，比如中文有常用的GBK编码，日文有Shift_JIS编码，如果没有历史遗留问题，强烈建议使用标准的`UTF-8`编码，所有语言使用同一种编码，既没有冲突，又被所有平台所支持。

不要使用Windows自带的记事本编辑任何文本文件。原因是Microsoft开发记事本的团队在保存UTF-8编码的文件时，他们在每个文件开头添加了0xefbbbf（十六进制）的字符，会遇到很多不可思议的问题。比如，网页第一行可能会显示一个“?”，明明正确的程序一编译就报语法错误，等等。建议使用Notepad++代替记事本，记得把Notepad++的默认编码设置为UTF-8 without BOM即可
##### 1. Git存储库初始化
* 新建仓库工作目录`yang`
* 将`yang`添加到Resource manager中
* 初始化仓库：View---Command palette---Git:Initialize Repository

##### 2. 暂存和提交
* 显示Git输出：Show Git Output
* 点击+号暂存所有更改：Stage Changes
* 提交到本地代码库：Commit
* 连接远程仓库`yang`：
> `git remote add origin https://github.com/yansicing/yang.git`<br>
> `git pull --rebase origin master`
* 代码合并后，最新的工作目录下面多了`LICENSE`和`README.md`
* 发布分支上传远程仓库：Publish Branch/Push
* 拉取：Pull
##### 3. 克隆远程仓库
* 在工作目录克隆远程代码仓库，然后用Visual Studio Code 打开

#### 为别人的开源项目贡献代码

Contributing
1.Fork it!
2.Create your feature branch: git checkout -b my-new-feature
3.Commit your changes: git commit -am 'Add some feature'
4.Push to the branch: git push origin my-new-feature
5.Submit a pull request

* 先点击 A 的项目仓库站点的`fork`的按钮
* 然后把你这个 fork 过来的仓库代码 Clone 检出
* 对该项目代码修改后，提交你的修改
* push到你的远程仓库
* 最后通过内建的`pull request`机制向项目负责人申请代码合并
* A 觉得你修改的代码写的很好，同意之后，你修改的代码就能合并到该项目


---

> 待完善（To be added~）

---


##### 参考文献 <span id="4">
- [git-tutorial](https://www.runoob.com/git/git-tutorial.html)
- [Windows10和Visual Studio Code环境中配置使用Git和GitHub](https://blog.csdn.net/fylstudio/article/details/79106331)
- [git终端合并代码的简单使用](https://www.jianshu.com/p/220c6846badf)
- [廖雪峰的官方网站-Git教程](https://www.liaoxuefeng.com/wiki/896043488029600/896827951938304)
- [Pro Git book](https://git-scm.com/book/zh/v2)
- [Git的详细使用教程——三部曲](https://blog.csdn.net/oman001/article/details/80208632)
- [Git使用教程,最详细，最傻瓜，最浅显，真正手把手教](https://blog.csdn.net/qq_36150631/article/details/81038485)
- [Git学习记录](https://strivebo.com/2019/02/12/%E7%89%88%E6%9C%AC%E6%8E%A7%E5%88%B6%20-%20%EF%BC%88%E4%B8%80%EF%BC%89Git%E5%AD%A6%E4%B9%A0%E8%AE%B0%E5%BD%95(%E4%B8%8D%E6%96%AD%E6%9B%B4%E6%96%B0)/)
- [GitHub支持的Markdown之文档写作指南](https://strivebo.com/2019/02/13/%E7%89%88%E6%9C%AC%E6%8E%A7%E5%88%B6%20-%20GitHub%E6%94%AF%E6%8C%81%E7%9A%84Markdown%E4%B9%8B%E6%96%87%E6%A1%A3%E5%86%99%E4%BD%9C%E6%8C%87%E5%8D%97/)
- []()
- []()




---
##### **返回[顶部](#home)**