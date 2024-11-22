---
title: "Fail2ban 一键脚本：快速配置 SSH 安全防护指南"
description: "通过 Fail2ban 脚本轻松提高 VPS 的 SSH 安全性，防止暴力破解攻击。详细教程包括更改端口、限制尝试次数及封禁时间配置，让服务器更安全。"
keywords: ["Fail2ban 脚本", "SSH 安全", "VPS 防护", "暴力破解防御", "Linux 安全工具", "Fail2ban 配置"]
author: "AJAXM"
date: 2024-11-22
categories: ["Linux 安全", "VPS 工具", "服务器防护"]
tags: ["Fail2ban", "SSH", "服务器安全", "VPS", "Linux"]
---

# 前言
从linux do的佬友总结帖发现的，非常的方便和便利。
帖子地址：[收集整理的2024最新的常用VPS脚本工具 - 开发调优 - LINUX DO](https://linux.do/t/topic/165688)

脚本工具：
```
wget https://raw.githubusercontent.com/FunctionClub/Fail2ban/master/fail2ban.sh && bash fail2ban.sh 2>&1 | tee fail2ban.log
```

输入后会出现选项：
更改 SSH 端口。
- 默认端口是 **22**，可选择更改为其他未被占用的端口（如 **2222** 或 **2022**）以提高安全性。
- 确保更新防火墙规则以开放新端口。
```
Do you want to change your SSH Port? [y/n]: 
```
尝试登录的最大失败次数
- 输入范围：**2-10**
- 设置尝试登录失败的次数，超出次数后 Fail2ban 会封禁该 IP。
```
Input the maximun times for trying [2-10]:  
```
封禁时长
- 输入单位：**小时**
- 设置被封禁 IP 的持续时间
```
Input the lasting time for blocking a IP [hours]:  
```
