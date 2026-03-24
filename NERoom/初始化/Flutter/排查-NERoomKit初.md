---
track_type: 排查类
sub_type: 集成类
product: NERoom
feature: 初始化
platform: Flutter
title: NERoomKit初始化失败后无法重试
root_cause: 重复初始化导致失败
solution: 确保初始化只执行一次，避免重复初始化
customers: ["河南新秀金文化传媒"]
source: chat_history
tags: ["NERoom", "初始化", "Flutter", "重复初始化"]
created: 2025-02-14
updated: 2026-03-20
---

## 问题：Flutter NERoomKit初始化失败后无法重试

## 问题详情

**现象**：
Flutter端NERoomKit初始化失败后，再次执行不会成功，必须重启APP。

## 排查过程

1. 检查初始化代码
2. 发现重复初始化问题
3. 确认初始化时机在登录后

## 问题原因

重复初始化导致失败

## 解决方案

确保初始化只执行一次，避免重复初始化

## 其他触发场景
- [Flutter] NERoomKit初始化失败后无法重试，来源：['河南新秀金文化传媒']，2026-03-20
- [Flutter] NERoomKit初始化失败后无法重试，来源：['河南新秀金文化传媒']，2026-03-20

