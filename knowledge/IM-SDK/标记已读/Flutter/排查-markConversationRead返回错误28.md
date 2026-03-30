---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 标记已读
platform: Flutter
title: markConversationRead返回错误28
root_cause: 
solution: 使用clearUnreadCountByIds方法按照会话ID批量将指定会话列表的消息未读数清零。
customers: ["VIP云信-四川斯特雅科技有限责任公司"]
source: chat_history
tags: ["标记已读", "错误28", "clearUnreadCountByIds", "Flutter"]
created: 2025-11-05
updated: 2026-03-20
---

## 问题：Flutter markConversationRead返回错误28

## 问题详情

**现象**：
调用markConversationRead方法标记会话已读，返回错误28。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 确认登录状态和会话ID；2. 检查conversationId格式是否正确；3. 验证方法调用时机。

**关键发现**：

## 问题原因



## 解决方案

使用clearUnreadCountByIds方法按照会话ID批量将指定会话列表的消息未读数清零。

## 其他触发场景

