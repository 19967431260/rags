---
track_type: 排查类
sub_type: 测试问题
product: IM-SDK
feature: 会话管理
platform: Android
title: deleteChattingHistory清空后会话显示空消息
root_cause: deleteChattingHistory只清理本地数据库，当所有消息被删除且无最后一条消息时，会话的lastMessage为空，这是预期行为
solution: deleteChattingHistory是清理本地数据库操作，不会生成空消息；如需删除单条消息应使用deleteMessage方法；lastMessage为空属正常现象
customers: ["上海抱朴"]
source: chat_history
tags: ["Android", "deleteChattingHistory", "空消息", "lastMessage", "会话列表"]
created: 2025-07-16
updated: 2025-07-25
---

## 问题：Android deleteChattingHistory清空后会话显示空消息

## 问题详情

**现象**：
Android端调用deleteChattingHistory后，会话列表中出现一条空消息（会话lastMessage为空）。

**环境信息**：
- SDK版本：IM V9 本地消息历史
- 问题场景：调用deleteChattingHistory删除消息后

**相关日志**：
服务端查询不到空文本消息记录。

## 排查过程

1. 客户提供SDK日志进行排查
2. 确认调用了deleteChattingHistory清空了消息
3. 明确deleteChattingHistory只清理本地数据库，与云端无关
4. 所有消息删除后，没有消息可以顶上，lastMessage为空
5. 服务端查询最近7天记录，未查到空文本消息

**关键发现**：deleteChattingHistory是清理本地数据库的操作，云端消息不受影响；当所有消息被删除后无最后一条消息，会话的lastMessage字段为空。

## 问题原因

deleteChattingHistory只清理本地数据库，不会生成空消息实例。当本地所有消息被删除后，会话的lastMessage为空，这是预期行为，非SDK异常。

## 解决方案

1. deleteChattingHistory是清理本地数据库的操作，不会生成空消息
2. 如需删除单条消息，应使用deleteMessage方法
3. 会话lastMessage为空属正常现象，可通过刷新会话列表UI刷新
4. 如需保留消息但隐藏显示，应使用消息撤回或标记已读等替代方案
