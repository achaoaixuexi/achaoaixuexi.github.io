---
title: "Hugo + Stack 主题搭建个人博客指南"
description: "从零开始，使用 Hugo 和 Stack 主题搭建一个美观、快速的个人博客网站。"
date: 2026-07-23T16:30:00+08:00
draft: false
tags: ["Hugo", "博客", "教程"]
categories: ["技术"]
image: 
math: false
license: 
comments: false
---

## 前言

一直想拥有一个属于自己的个人博客，用来记录学习心得和生活感悟。经过一番调研，最终选择了 **Hugo** + **Stack 主题** 这个组合。这篇文章记录了我的搭建过程，希望能帮助到有同样需求的朋友。

## 为什么选择 Hugo？

[Hugo](https://gohugo.io/) 是用 Go 语言编写的静态网站生成器，有以下几个突出优点：

- **极速构建**：数百篇文章也能在毫秒级完成构建
- **单二进制文件**：无需安装 Node.js、Python 等运行时依赖
- **丰富的主题生态**：社区提供了大量高质量主题
- **Markdown 写作**：用 Markdown 撰写文章，简单高效

## 为什么选择 Stack 主题？

[Stack 主题](https://github.com/CaiJimmy/hugo-theme-stack) 是目前 Hugo 社区最受欢迎的博客主题之一：

- 🎨 **简洁现代的设计**：左侧个人信息卡片 + 右侧文章列表的经典布局
- 🌙 **暗色模式支持**：自动适应系统主题，也可手动切换
- 📱 **响应式设计**：完美适配手机、平板和桌面端
- 🔍 **内置搜索**：支持文章全文搜索
- 🏷️ **标签和分类**：方便组织和管理文章

## 快速上手步骤

### 1. 安装 Hugo

```bash
# Windows (使用包管理器)
winget install Hugo.Hugo.Extended

# macOS
brew install hugo

# Linux
sudo apt install hugo
```

### 2. 创建站点

```bash
hugo new site myblog
cd myblog
```

### 3. 安装主题

```bash
git clone https://github.com/CaiJimmy/hugo-theme-stack.git themes/hugo-theme-stack
```

### 4. 创建第一篇文章

```bash
hugo new post/hello-world/index.md
```

编辑生成的 Markdown 文件，将 `draft: true` 改为 `draft: false` 即可发布。

### 5. 本地预览

```bash
hugo server -D
```

打开浏览器访问 `http://localhost:1313` 就能看到你的博客了！

## 部署到 GitHub Pages

将博客部署到 GitHub Pages 可以免费托管你的个人网站：

1. 在 GitHub 创建 `<username>.github.io` 仓库
2. 将博客代码推送到仓库
3. 在仓库 Settings → Pages 中启用 GitHub Actions
4. 每次推送代码，GitHub Actions 会自动构建并部署

## 小结

Hugo + Stack 主题的组合让我在很短的时间内就搭建好了个人博客。整个过程简单流畅，即使没有太多前端经验也能轻松上手。接下来就是坚持写作了！✍️

---

> 如果你也在搭建个人博客，欢迎在评论区交流讨论～
