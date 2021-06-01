---
title: "nvm npm cnpm nrm的区别"
date: 2021-05-31T17:21:12+08:00
tag: ["Node"]
---

# 前言

我们知道，下载安装node.js后我们就拥有了npm这一命令行工具。然后只要了解npm install, npm start等简单的命令后，我们就可以愉快的投入开发了。但如果我们经常在不同的网络环境下工作，或需要同时处理多个依赖node版本不同的项目时，单纯靠npm工作仍然会感到有诸多不便之处，例如：

**情况A**

我们可能会需要开发多个项目，有的新的项目可能用最新版本的Node进行开发，而有些老的项目因为历史久远，依赖的还是低版本的Node。 如果同时开发这几个项目，且仅靠npm的话，我们就不得不来回下载全局唯一的Node包，这会浪费大量开发时间

**情况B**

​		在开发中我们可能经常需要切换npm源，默认的npm源是[https://registry.npmjs.org/](https://link.zhihu.com/?target=https%3A//registry.npmjs.org/), 但有时我们会因外墙的原因下载很慢，这时我们可能会切换到淘宝源或者cnpm源。而在另外一些时候，我们可能会需要安装公司内部使用的npm包，这时我们又会切换到公司私有的npm源。我们可以采用npm config set registry --url这样的方式手动切换，但使用却有些不方便，而且众多地址也不利于管理。

# nvm

> nvm是让你在同一台机器上安装和切换不同mode版本的管理工具,为了解决node各种版本存在不兼容现象

- window安装方法： 直接下载安装包安装：[https://github.com/coreybutler/nvm-windows/releases](https://links.jianshu.com/go?to=https%3A%2F%2Fgithub.com%2Fcoreybutler%2Fnvm-windows%2Freleases)，选择nvm-setup.zip，下载后直接安装。安装成功后打开命令行，执行nvm -v命令检查安装是否成功
- mac下面的安装，其实就可以按照linux的安装就可以了！安装的命令我们可以在nvm的github的资源上面得到安装方法：

```
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.8/install.sh | bash
```

> nvm常用命令

`nvm install v10.4.0`：安装指定版本号的node使用

`nvm ls-remote`：列出所有可以安装的node版本号

`nvm ls`：列出所有已经安装的node版本

`nvm use v10.3.0`：切换node的版本，这个是全局的`nvm current`：当前node版本

# npm

> NPM是随同NodeJS一起安装的包管理工具，能解决NodeJS代码部署上的很多问题,由于新版的nodejs已经集成了npm，所以之前npm也一并安装好了。可以通过输入 "npm -v" 来测试是否成功安装。

`npm install <Module Name>`: 本地安装 Node.js 模块

`npm install <Module Name> -g`: 全局安装Node.js 模块

`npm search <Module Name>` : 搜索模块

`npm update <Module Name>`: 更新模块至最新版本

`npm list`: 查看当前所有安装的模块：

`npm list <Module Name>`: 查看某个模块的版本号

`npm init`: 创建模块

# cnpm

> cnpm，它是中国版的npm镜像库，地址在这里：https://cnpmjs.org/，也是npm官方的一个拷贝，因为我们和外界有一堵墙隔着，所以用这个国内的比较快，淘宝也弄了一个和npm一样的镜像库，http://npm.taobao.org/，它和官方的npm每隔10分钟同步一次。

- 安装方式：

```
npm install -g cnpm –registry=http://r.cnpmjs.org
// 或者用淘宝
npm install -g cnpm –registry=https://registry.npm.taoba.org
```

安装好了cnpm后，直接执行`cnpm install 包名`。比如：cnpm install bower -g 就可以了。-g只是为了把包安装在全局路径下。如果不全局安装，也可以在当前目录中安装，不用-g就可以了。

# nrm

> nrm(npm registry manager )是npm的镜像源管理工具，有时候国外资源太慢，使用这个就可以快速地在 npm 源间切换

- 执行命令: `npm install -g nrm`全局安装nrm

> nrm 常用命令

`nrm ls` : 查看可选的源

`nrm use taobao`: 切换到taobao源

`nrm add registry http://registry.npm.frp.trmap.cn/`: 你可以增加定制的源，特别适用于添加企业内部的私有源，执行命令 nrm add <registry> <url>，其中reigstry为源名，url为源的路径

`nrm del <registry>` : 删除对应的源

`nrm test`: 测试相应源的响应时间