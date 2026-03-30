---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 本地数据库
platform: Web
title: Web端数据库写入错误
root_cause: 疑似磁盘空间不足导致数据库无法写入
solution: 检查磁盘空间是否已满，清理后重试
customers: ["格致诚心"]
source: chat_history
tags: ["Web", "数据库", "db::addTask", "磁盘满"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：Web端数据库写入错误

## 问题详情

**现象**：
客户反馈Web端出现db::addTask错误，提示isTrusted事件。

**环境信息**：
- 平台：Web

## 排查过程

1. 日志信息不足需补充
2. 推测可能磁盘满导致数据库写入失败

## 根因分析

疑似磁盘空间不足导致数据库无法写入

## 解决方案

检查磁盘空间是否已满，清理后重试

## 其他触发场景

（无）
