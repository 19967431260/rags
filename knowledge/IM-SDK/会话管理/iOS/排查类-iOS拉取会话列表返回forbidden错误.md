---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 会话管理
platform: iOS
title: iOS拉取会话列表返回forbidden错误
root_cause: 套餐续期后部分配置被重置，云端会话功能开关被关闭。
solution: 在控制台开启云端会话功能开关，旗舰版支持云端会话功能。
customers: ['海南无限链科技有限公司']
source: chat_history
tags: ['iOS', '会话列表', 'forbidden', '云端会话', '开关配置']
created: 2025-01-02
updated: 2026-03-23
---

## 问题：iOS拉取会话列表返回forbidden错误

## 问题详情

**现象**：
iOS端突然拉不回来会话列表，创建会话返回forbidden错误。

## 排查过程

1. 确认IM套餐版本为旗舰版；2. 检查云端会话功能开关；3. 发现开关未开启。

## 问题原因

套餐续期后部分配置被重置，云端会话功能开关被关闭。

## 解决方案

在控制台开启云端会话功能开关，旗舰版支持云端会话功能。

## 其他触发场景

（合并时在此处追加）
