---
track_type: 排查类
sub_type: 使用问题
product: 网易会议
feature: 初始化
platform: Windows
title: Electron会议组件初始化速度慢问题
root_cause: chromium读取配额数据库时，多个进程同时读取造成阻塞
solution: 确保应用退出时清理残留进程。优化版本已提供，初始化时间约3s。
customers:
  - 深圳联友
source: chat_history
tags:
  - Electron
  - 初始化
  - 速度慢
  - 进程
  - chromium
created: '2025-06-10'
updated: '2025-03-23'
---

## 问题：Windows Electron会议组件初始化速度慢问题

## 问题详情

**现象**：
Electron会议组件初始化时，第一次约3s，但后续启动如果进程未完全退出，初始化速度会很慢（10s以上）。

**排查过程**：

1. 确认杀掉所有进程后初始化速度正常（3s左右）
2. 发现残留进程影响初始化速度
3. 怀疑是chromium读取配额数据库引起，同时多个进程读取造成
4. 提供测试包验证

**关键发现**：chromium读取配额数据库时，多个进程同时读取造成阻塞

## 问题原因

chromium读取配额数据库时，多个进程同时读取造成阻塞

## 解决方案

确保应用退出时清理残留进程。优化版本已提供，初始化时间约3s。
