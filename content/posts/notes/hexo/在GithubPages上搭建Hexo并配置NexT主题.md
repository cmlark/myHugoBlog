---
title: 在GithubPages上搭建Hexo并配置NexT主题
tags: ["GithubPages", "Hexo", "Blog"]
categories: Hexo
draft: false
date: 2022-04-10T16:10:10+08:00
---

## 在 GithubPages 上搭建 Hexo 并配置 NexT 主题

#### 啰里啰唆

记录一下自己搭建 blog 的过程，之前在 vps 上配置过 word press，但是一直也没更新，而且好的 vps 很贵维护成本也很高，索性干脆不用了，就尝试一下使用 hexo 在 github 上搭建 blog，效果还不错，总共也就历时两天。网上类似的教程也很多，这里总结记录一下，方便以后开新坑

#### 首先安装 Node.js 和 Git for Windows

[Node.js 官网]([Node.js (nodejs.org)](https://nodejs.org/en/))，[Git for windows 官网]([Git (git-scm.com)](https://git-scm.com/))，Node.js 建议安装 LTS 长期支持版，支持周期更长且更稳定

Node.js:点击第一个绿色的按钮下载 Node.js,版本不需要和图示一致，直接下载最新版即可。

![LkbK0K.png](https://s1.ax1x.com/2022/04/10/LkbK0K.png)

Git:点击网页左侧小电脑当中的 Download for windows，直接下载最新版即可无需与图示中版本一致。

![LkbmOx.png](https://s1.ax1x.com/2022/04/10/LkbmOx.png)

下载完成后按照默认安装设置安装即可。

#### 在 GitHub 上创建一个仓库

首先，需要一个 GitHub 账号。打开 GitHub 官网点击左上角的 sign in 就能注册了，不复述了很简单。进行这个过程可能需要**科学**上网，具体自行百度。

**创建一个 Github 仓库**

点击左上角头像，在弹出的下拉菜单中选择 **Your repositories**，待页面加载完毕后点击左上角绿色的**new**创建一个仓库。

![Lkbum6.png](https://s1.ax1x.com/2022/04/10/Lkbum6.png)

**注意**：仓库名务必是**==你的用户名.github.io==**,比如上面我的用户名是 ivy-lun,那么仓库名就是 ivy-lun.github.io,其他的保持默认即可，点击绿色按钮 Create repositories 即可创建一个仓库。

# 太累了，过两天再更吧
