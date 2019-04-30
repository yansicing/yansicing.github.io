---
title: Github Pages Blog
layout: post
categories: Website
tags: Github-pages Blog
excerpt: Jekyll builds github pages personal blog website
---
#### Jekyll搭建Github Pages个人博客 <span id="home">
---

#### 目录 <span id="home">

* [引言](#1)
	* [关于博客](#1.1)
	* [关于Github](#1.2)
* [创建Github账号](#2)
* [创建仓库](#3)
	* [填充仓库](#3.1)
	* [配置Github Pages功能](#3.2)
* [博客上传](#4)
	* [Git基础](#4.1)
	* [git配置](#4.2)
	* [git Desktop版](#4.3)
* [创建本地仓库](#5)
* [安装Jekyll](#6)
	* [关于Jekyll](#6.1)
	* [安装步骤](#6.2)
	* [开启jekyll](#6.3)
* [博客写作](#7)
	* [Markdown基础](#7.1)
	* [工具介绍](#7.2)
	* [图床介绍](#7.3)
	* [图片尺寸](#7.4)
* [域名配置](#8)

---------------

#### __引言__ <span id="1">

##### 关于博客 <span id="1.1">
- 写博客是个比较好的习惯，你可以`分享心得、发表看法、记录笔记`···

- 人类除了`衣食住行`以外，还有几样重要的东西：`爱心`与`知识`···

- `开源`是一种态度，`分享`是一种精神、一种情怀!

**开源领域重要人物**
- `理查德·马修·斯托曼`（Richard Matthew Stallman, 1953~）——自由软件运动，创立GNU, FSF, GPL 
- `林纳斯·本纳第克特·托瓦兹`（Linus Benedict Torvalds, 1969~ ）——创造Linux，Git

我们可以结合`CSDN博客`和`Github Pages`的独立个人博客网页进行博客写作

##### 关于Github Pages<span id="1.2">

- [GitHub]：分布式版本控制系统，面向开源及私有软件项目的托管平台
- [SVN]：集中式版本控制系统，Git是SVN的发展版，现在主流也是Git，但某些大公司依然在使用SVN
- [Github Pages]：是Github上的一项功能，可以放置网页文件到指定文件夹，然后分配一个专属域名用于展示一些项目，也可用来开发个人博客网站

#### __创建Github账号__ <span id="2">

Github Pages 功能依赖于Github账号，需要在[Github官网][Github-register] 注册(sign up)

#### __创建仓库__ <span id="3">

创建仓库`repository`后，可以上传文件到这个目录下，我们用这个仓库来使用Github Pages功能 
 
##### 填充仓库 <span id="3.1">

仓库里面存放着支撑博客首页的一些网页文件和配置文件，可以选择已有的[jekyllthemes](http://jekyllthemes.org/)主题

##### 配置Github Pages功能 <span id="3.2">

点击刚新建的`repository`，进入`Settings`，重命名为：`yansicing.github.io`

#### __博客上传__ <span id="4">

##### Git基础 <span id="4.1">
- 使用`git`向github仓库上传文件，进行`提交、拉取、克隆`等操作：[Git下载地址](https://git-scm.com/)
- git基本操作：`git commit` , `git push`, `git clone` 等，可参见完整教程：[Git语法说明][git-full]

##### Git配置 <span id="4.2">

* 安装好后`cmd`输入 `git` 有反应则安装成功
* 配置`昵称`和注册`邮箱`

```
git config --global user.name "YOUR NAME"
git config --global user.email "YOUR EMAIL ADDRESS"
```

* 在`git bash `软件下输入如下命令生成令牌，本地和Github 一份，这样 Github 可以在你使用仓库时校验确定你的身份

```
cd ~/.ssh
mkdir key_backup
ssh-keygen -t rsa -C "*your_email@youremail.com*"
```

* 使用命令 `cat id_rsa.pub` 再将内容复制到剪切板，然后进入Github账号`Settings`里面，选择`添加SSH key`，粘贴在Key中，Title随意取
- 输入 `ssh -T git@github.com` 测试连通状态

##### Git Desktop版 <span id="4.3">

Git还能使用https协议连接，只不过要每次输入账号和密码，但是可以选择Github官方提供的`Github Desktop`软件

#### __创建本地仓库__ <span id="5">
- 选择一个本地文件夹，用作保存本地仓库文件，尽量是空文件夹

- 然后使用命令 `git init` 初始化文件夹，会在当前文件夹下生成`.git` 的隐藏文件夹，里面是一些配置文件，不要随意更改

- 使用 `git clone https://github.com/name/repository.git` 将远程仓库克隆到本地此文件夹下
`name` 是自己的昵称，`repository` 是自己的仓库名

- 然后此文件夹下会多一个和你仓储名一样的文件夹，内部文件与远程仓库一样

- 绑定远程仓库，方便提交：

	`git remote add origin git@github.com:username/username.github.io.git`

- 常用命令：
```
	git add .                        // 添加文件
	git commit -m "commit-messages"  // 提交本地仓库
	git push origin master           // 提交远程仓库
	git pull                         // 拉取远程文件，与以下命令类似
	git branch temp                  // 创建本地分支
	git fetch origin master:temp
	git merge master
```

#### __安装Jekyll__ <span id="6">

##### 关于Jekyll <span id="6.1">

Jekyll是一个简单免费的生成博客网页的工具，可以绑定Github，详情参考：
- [jekyllrb-English](https://jekyllrb.com/)
- [jekyll-Chinese](https://www.jekyll.com.cn/)
- 类似的工具：[hexo](https://hexo.io/zh-cn/)

>###### 上传修改后的文件到Github仓库后需要一段时间才能看到修改效果，所以可以选择安装本地Jekyll工具进行本地快速预览

##### 安装步骤 <span id="6.2">

* **安装[Ruby](http://www.ruby-lang.org/en/downloads/)**：Jekyll依赖于Ruby，需提前安装
* **安装[gem](https://rubygems.org/pages/download)**：cmd输入： `gem` 检查是否安装成功，安装ruby后自带gem（貌似~）
* **安装jekyll**：cmd输入： `gem install jekyll`

##### 开启Jekyll <span id ="6.3">

- 直接输入 `jekyll s` 开启jekyll服务，windows可能会有问题
- 可以尝试 `bundle exec jekyll s` 命令，如果提示没有安装 `bundler` ，就 `gem install bundler` 再 `bundle install`
- 可能还会提示没有安装其他组件`xx`，`gem install xxx` 即可
- 然后就可以成功运行，退出按 `ctrl + c ` 
- 运行时保持窗口不要关闭，浏览器输入 `127.0.0.1:4000` 或 `localhost:4000` 预览
- windows预览效果可能不好，加载不出图片，其他系统没试过

#### __博客书写__<span id="7">

##### Markdown基础 <span id="7.1">
Jekyll使用[Markdown][markdown]语言书写博客，Markdown是一种简单易读的标记性语言

##### 工具介绍 <span id="7.2">
每次都用编辑器写好 `.md` 文件，然后用 `git` 上传到 Github 根目录下的 **`_post`** 文件夹有些繁琐

Jekyll官方提供了博客编辑器[jekyllwriter](http://jekyllwriter.com)，方便书写、预览、上传

- 安装后主界面：

![jekyll-writer.jpg](http://yansicing.net3v.net/jekyll-writer.jpg)

- 安装后需要`添加账号，配置 token，生成token，粘贴进输入框`
- 写完后保存并上传
- 可以在`Open Post List`查看和修改账户下的博客

##### 图床介绍 <span id="7.3">
你可以将自己的图片上传到它的网站，然后它返回图片的链接，插入博客中即可显示图片
- 推荐一个知名的：[七牛云](https://portal.qiniu.com/)，需要在备案并在jekyll writer中配置
- 还有一个神奇的：[sm.ms](https://sm.ms/)
- [CSDN](https://mp.csdn.net/)在线编辑器，图片能直接上传到CSDN上，直接生成链接

##### 图片尺寸 <span id="7.4">
Markdown的图片插入方式 `![title](http://xxx.com/xxx.png/)` 是无法修改图片尺寸的

可以使用`html`中的 `<img>`标签：
`<img src="http://xxx.com/xxx.png/" alt="title" width=XXpx height=XXpx>`

#### __域名配置__ <span id="8">

此时该网站不能被百度等搜索引擎搜到，百度是禁止抓取 Github Pages 内容的

可以购买一个自己的专属域名：[阿里云](https://www.aliyun.com/)、[腾讯](https://cloud.tencent.com/)、[花生壳](https://console.oray.com/)等

百度站长平台有个链接提交功能，但是它只是加速爬取，并未解决收录，貌似它们的`熊掌号`服务可以解决

再添加两条 Github 的ip的 A记录值 ：`192.30.252.153` ，`192.30.252.154`

>最后搜索: `"site:你的域名"` 有结果就成功了

__[Start your blog now~](http://yansicing.github.io)__

##### __参考文献__ <span id="4">
- [KNIGH_YUN](https://blog.csdn.net/KNIGH_YUN/article/details/79774344)

----------------
[Github]: https://baike.baidu.com/item/github/10145341
[SVN]: https://baike.baidu.com/item/SVN/3311103?fr=aladdin
[Github Pages]:https://pages.github.com/
[github-register]: https://github.com/
[markdown]: https://baike.baidu.com/item/markdown/3245829?fr=aladdin
[git-full]: https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000
[markdown-full]: https://blog.csdn.net/KNIGH_YUN/article/details/79733814
[markdown-tutorial]: <https://blog.csdn.net/KNIGH_YUN/article/details/79718481>

##### **返回[顶部](#home)**