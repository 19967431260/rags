---
track_type: 排查类
sub_type: 使用问题
product: IM-UIKit
feature: 会话列表
platform: Uniapp
title: UIKit getMsg偶尔查不到消息
root_cause: getMsg只从内存读取，刷新后消息可能未同步到内存
solution: 使用getHistoryMsgActive获取历史消息；初始化时enableV2CloudConversation设为true使用云端会话
customers: ["VIP云信-广州鲸听科技有限公司"]
source: chat_history
tags: ["getMsg", "历史消息", "UIKit", "Uniapp"]
created: 2025-11-07
updated: 2026-03-20
---

## 问题：Uniapp UIKit getMsg偶尔查不到消息

## 问题详情

**现象**：
uni.$UIKitStore.msgStore.getMsg(conversationId)有时查不到消息列表。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 检查版本
2. 分析原因 → getMsg只从内存取
3. 建议方案 → 使用getHistoryMsgActive
**关键发现**：getMsg只读取内存，可能未同步

**关键发现**：

## 问题原因

getMsg只从内存读取，刷新后消息可能未同步到内存

## 解决方案

使用getHistoryMsgActive获取历史消息；初始化时enableV2CloudConversation设为true使用云端会话

## 其他触发场景

