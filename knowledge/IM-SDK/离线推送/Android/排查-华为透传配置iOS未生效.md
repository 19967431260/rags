---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 离线推送
platform: Android
title: 华为透传配置iOS未生效
root_cause: 华为透传消息的collapse_key参数类型错误，应使用number类型而非string
solution: 将collapse_key设置为-1（number类型），参考华为透传消息文档配置
customers: ['北京爱豆文化传媒有限公司']
source: chat_history
tags: ['华为推送', '透传', 'collapse_key', 'iOS']
created: 2025-02-11
updated: 2026-03-23
---

## 问题：Android 华为透传配置iOS未生效

## 问题详情

**现象**：
iOS配置payload时使用华为透传配置未生效，Android可以调通。

**环境信息**：
- 平台：Android
- 产品：IM-SDK

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 检查collapse_key参数 → 发现配置错误
2. 检查参数类型 → 华为服务器反馈值类型错误，应使用number而非string
3. 关键发现：collapse_key应设置为-1（number类型）

## 问题原因

华为透传消息的collapse_key参数类型错误，应使用number类型而非string

## 解决方案

将collapse_key设置为-1（number类型），参考华为透传消息文档配置

## 其他触发场景

（合并时在此处追加：`- [Android] 华为透传配置iOS未生效，来源：['北京爱豆文化传媒有限公司']，2026-03-23`）
