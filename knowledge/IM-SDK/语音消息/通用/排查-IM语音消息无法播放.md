---
track_type: 排查类
sub_type: 功能异常
product: IM-SDK
feature: 语音消息
platform: 通用
title: IM语音消息无法播放
root_cause: 文件存储URL在内网环境无法访问
solution: 检查文件存储URL的网络访问权限，确保内网环境可以访问
customers: ["ISV云信-恒生芸泰-互联网医院-dx"]
source: chat_history
tags: ["语音消息", "无法播放", "内网环境"]
created: 2025-12-08
updated: 2026-03-23
---

## 问题：IM语音消息无法播放

## 问题详情

**现象**：
医生反馈在IM界面可以看到患者语音信息，但是无法点开播放。

**环境信息**：
- 产品：IM-SDK
- 功能：语音消息

## 排查过程

1. 确认服务正常
2. 怀疑是文件存储URL在内网环境无法打开

**关键发现**：文件存储URL在内网环境无法访问

## 问题原因

文件存储URL在内网环境无法访问。

## 解决方案

检查文件存储URL的网络访问权限，确保内网环境可以访问。

## 其他触发场景

