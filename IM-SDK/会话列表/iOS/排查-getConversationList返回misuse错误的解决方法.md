---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 会话列表
platform: iOS
title: getConversationList返回misuse错误的解决方法
root_cause: 未设置enableV2CloudConversation开关，默认关闭导致获取云端会话失败
solution: 在初始化V2NIMSDKOption时设置v2Option.enableV2CloudConversation = true（或V2NIMCloudConversationSwitch），开启云端会话功能后再调用getConversationList
customers: ["吉林省大塘网络科技有限公司"]
source: chat_history
tags: ["getConversationList","iOS","misuse","云端会话","enableV2CloudConversation"]
created: 2025-08-01
updated: 2026-03-26
---

## 问题：iOS getConversationList返回misuse错误的解决方法

## 问题详情

**现象**：
iOS端调用getConversationList获取云端会话列表，返回error: misuse。

**复现步骤**：
（无明确步骤，从会话提取）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

（无详细排查步骤，从会话提取）

**关键发现**：未设置enableV2CloudConversation开关，默认关闭导致获取云端会话失败

## 问题原因

未设置enableV2CloudConversation开关，默认关闭导致获取云端会话失败。

## 解决方案

在初始化V2NIMSDKOption时设置v2Option.enableV2CloudConversation = true（或V2NIMCloudConversationSwitch），开启云端会话功能后再调用getConversationList。

## 其他触发场景

（合并时在此处追加）
