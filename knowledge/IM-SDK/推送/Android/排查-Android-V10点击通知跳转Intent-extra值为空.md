---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 推送
platform: Android
title: Android V10点击通知跳转Intent extra值为空
root_cause: 荣耀设备onNewIntent extra字段缓存问题
solution: 1. 使用启动页接收跳转；2. 使用NimIntent.EXTRA_NOTIFY_CONTENT解析消息；3. 参考demo示例代码
customers: ["江阴伍壹零传媒"]
source: chat_history
tags: ["推送", "Android", "Intent", "extra", "荣耀"]
created: 2025-11-03
updated: 2026-03-20
---

## 问题：Android Android V10点击通知跳转Intent extra值为空

## 问题详情

**现象**：
客户反馈Android V10点击通知跳转后Intent没有extra值，以及会话分组添加问题。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客户反馈点击通知跳转Intent extra为空
2. 发现荣耀设备onNewIntent extra字段不会更新
3. 建议换启动页或空activity处理
4. 提供NimIntent.EXTRA_NOTIFY_CONTENT解析方式

**关键发现**：

## 问题原因

荣耀设备onNewIntent extra字段缓存问题

## 解决方案

1. 使用启动页接收跳转；2. 使用NimIntent.EXTRA_NOTIFY_CONTENT解析消息；3. 参考demo示例代码

## 其他触发场景

