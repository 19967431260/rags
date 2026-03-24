---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 本地消息
platform: iOS
title: 插入本地消息后lastMessage不更新
root_cause: 被撤回的消息未删除，导致lastMessage仍显示原消息
solution: 调用deleteMessage删除被撤回的消息，或抽离demo进一步排查
customers: ['武汉友趣网络科技']
source: chat_history
tags: ['本地消息', 'lastMessage', 'iOS', 'deleteMessage']
created: 2025-01-15
updated: 2026-03-23
---

## 问题：iOS 插入本地消息后lastMessage不更新

## 问题详情

**现象**：
iOS端写入本地消息后，会话列表NIMRecentSession对象的lastMessage不是这条消息，重新运行App后获取的lastMessage是原本已撤回的消息。

## 排查过程

1. 客户反馈插入本地消息后lastMessage不更新
2. 技术支持询问插入时消息时间戳设置
3. 客户确认未设置时间戳
4. 技术支持建议手动设置时间戳，与被撤回消息时间戳保持一致
5. 客户尝试后仍不行
6. 技术支持建议删除被撤回的消息后再试
7. 客户尝试后仍一样
8. 技术支持建议抽离demo测试

## 问题原因

被撤回的消息未删除，导致lastMessage仍显示原消息

## 解决方案

调用deleteMessage删除被撤回的消息，或抽离demo进一步排查

## 其他触发场景

（合并时在此处追加）
