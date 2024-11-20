---
layout: post
title: 使用python获取hacker news当日新闻转换成markdown并自动上传至github pages
category: python
tags:
  - vps

description: python
keywords: github
date: 2024-11-04T23:19:54+08:00
id: 20241104
---

## 项目简介
该项目是一个自动化脚本，用于定时获取 Hacker News 当日热门新闻并推送至指定的 GitHub 仓库。通过 GitHub Actions 或本地调度，该脚本会每 3 小时从 Hacker News 获取最新的热门新闻，自动翻译成中文，并生成 Markdown 格式的新闻更新文件。如果当天文件尚不存在，它会创建一个带头部信息的文件；如果已存在，则仅更新内容部分。适合搭建个人博客每日新闻推送等应用。

## 功能说明
- **定时获取 Hacker News 热门新闻**：每 3 小时运行一次，获取最新 50 条当天新闻。
- **标题自动翻译**：使用 Google 翻译 API 将英文标题翻译为中文。
- **Markdown 文件生成**：如果是当天首次创建文件，生成包含头部信息的 Markdown 文件；否则，仅追加新闻内容。
- **自动推送到 GitHub**：将更新的文件推送至 GitHub 仓库，可用于静态博客每日新闻更新。

## 使用指南
1. **配置 GitHub 仓库**：在 `GITHUB_REPO` 中设置你要推送到的 GitHub 仓库地址（如 `username/repository`）。
2. **配置 GitHub Token**：在 `GITHUB_TOKEN` 中填入你的 GitHub 访问令牌，确保有写入权限。
3. **安装依赖**：
   ```
   pip install requests schedule googletrans==4.0.0-rc1 PyGithub
   ```
   
## 先决条件

**Python 3.x**：确保你已经安装了 Python 3.x。
**安装依赖库**：
   运行以下命令安装脚本所需的 Python 库：
   ```
   pip install requests schedule googletrans==4.0.0-rc1 PyGithub
   ```
**配置脚本**
配置 GitHub 仓库：

GITHUB_REPO：替换为你自己的 GitHub 仓库路径，例如 "username/repository"。
GITHUB_TOKEN：生成并替换为你自己的 GitHub 个人访问令牌（Token）。你可以在 GitHub 的 Settings > Developer settings > Personal access tokens 中生成 Token。
GITHUB_DIR_PATH：指定你希望存放 Markdown 文件的 GitHub 仓库中的目录路径。例如，"posts/hacknews"。
Hacker News API：
HACKERNEWS_API 默认已经配置为 Hacker News API 地址，无需修改

**后台启动**
首先在服务器安装screen：
```
sudo apt install screen
```

启动一个新的会话：
```
screen -S hackernews_session
```

在会话中运行脚本：
```
python hackernewsbot.py
```
可以将screen会话分离：
按下 Ctrl + A，然后按 D，分离会话

重新连接会话：
```
screen -r hackernews_session
```