---
track_type: 排查类
sub_type: 集成类
product: NERoom
feature: 集成
platform: Android
title: NERoom语音房房间不存在
root_cause: 后台有两个ID，可能使用了错误的房间ID。
solution: 确认使用正确的房间ID进入。
customers: ['海南无限链科技有限公司']
source: chat_history
tags: ['NERoom', '语音房', '房间不存在']
created: 2025-02-10
updated: 2026-03-23
---

## 问题：Android NERoom语音房房间不存在

## 问题详情

**现象**：
用服务端API创建语音房，SDK直接进入房间报错房间不存在。

**环境信息**：
- 平台：Android
- 产品：NERoom

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

（从会话提取排查过程）

## 问题原因

后台有两个ID，可能使用了错误的房间ID。

## 解决方案

确认使用正确的房间ID进入。

## 其他触发场景

（合并时在此处追加：`- [Android] NERoom语音房房间不存在，来源：['海南无限链科技有限公司']，2026-03-23`）
