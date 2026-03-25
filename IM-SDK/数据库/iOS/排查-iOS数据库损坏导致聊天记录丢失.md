---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 数据库
platform: iOS
title: iOS数据库损坏导致聊天记录丢失
root_cause: 数据库文件损坏
solution: 启用数据库备份NIMSDKConfig sessionDatabaseBackupEnabled设置为YES，已损坏数据无法恢复
customers: ["北京久幺幺"]
source: chat_history
tags: ["数据库损坏", "聊天记录丢失", "malformed", "iOS"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：iOS数据库损坏导致聊天记录丢失

## 问题详情

**现象**：
用户反馈聊天记录丢失，进入会话界面空白，数据库报错database disk image is malformed

**环境信息**：
- 平台：iOS

## 排查过程

1. 检查用户日志发现数据库损坏错误
2. 确认数据库文件异常

## 根因分析

数据库文件损坏

## 解决方案

启用数据库备份NIMSDKConfig sessionDatabaseBackupEnabled设置为YES，已损坏数据无法恢复

## 其他触发场景

（无）
