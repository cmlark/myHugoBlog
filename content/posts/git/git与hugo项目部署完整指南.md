---
date: "2025-03-22T17:35:40+08:00"
draft: false
title: "Git与hugo项目部署完整指南"
tags: [git, Github]
categories: Github
---

## 1. Git 基本操作与缓存管理

### 1.1 移除已跟踪文件的缓存

```bash
# 从Git移除文件跟踪但保留本地文件
git rm --cached <文件路径>

# 递归移除目录
git rm --cached <目录路径> -r
```

## 1.2 更新.gitignore 规则

```bash
添加需要忽略的目录/文件到.gitignore
echo "public/" >> .gitignore
echo "resources/" >> .gitignore
```

## 1.3 提交.gitignore 变更

```bash
git add .gitignore
git commit -m "更新忽略规则"
1.3 历史记录清理（慎用）
```

## 1.4 从所有提交历史中彻底删除文件

```bash
git filter-branch --force --index-filter \
  "git rm --cached --ignore-unmatch <文件路径>" \
  --prune-empty --tag-name-filter cat -- --all
```

# 2. Hugo 项目提交到 GitHub

## 2.1 标准提交流程

```bash
git init
git remote add origin https://github.com/<用户名>/<仓库>.git
git add .
git commit -m "初始提交"
git push -u origin main
```

## 2.2 推荐.gitignore 配置

```txt
Hugo生成文件
/public
/resources
.hugo_build.lock

# 系统文件
.DS_Store
Thumbs.db

# 开发环境
node_modules/
.idea/
```

## 2.3 多平台构建注意事项

1.部署平台需配置：
Hugo 扩展版环境变量

```bash
HUGO_VERSION=0.120.4
```

2.构建命令建议：

```bash
hugo --gc --minify --cleanDestinationDir
```

# 3. Git 子模块管理与主题集成

## 3.1 添加主题子模块

```bash
git submodule add https://github.com/adityatelange/hugo-PaperMod.git themes/papermod
```

## 3.2 子模块更新维护

```bash
# 更新子模块到最新版本
cd themes/papermod
git checkout master && git pull
cd ../..
git add themes/papermod
git commit -m "更新主题版本"
```

## 3.3 克隆包含子模块的仓库

```bash
git clone --recursive <仓库URL>
# 或分步操作
git clone <仓库URL>
git submodule init
git submodule update
```

# 4. SSH 密钥配置与认证问题

## 4.1 生成 ED25519 密钥

```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```

## 4.2 密钥部署流程

复制公钥内容

```bash
pbcopy < ~/.ssh/id_ed25519.pub
```

GitHub 添加路径：

```bash
Settings → SSH and GPG keys → New SSH Key
```

## 4.3 连接测试与代理配置

```bash
ssh -T git@github.com
# 设置SSH代理
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
```

# 5. Git 推送冲突解决方案

## 5.1 分支名称不匹配修复

```bash
# 重命名本地分支
git branch -m master main

# 强制推送分支转换
git push -u origin main -f
5.2 历史合并冲突处理

git pull origin main --allow-unrelated-histories
# 解决冲突后
git push origin main
```
