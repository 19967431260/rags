---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 会话管理
platform: Uniapp
title: 会话名称显示为teamid且头像为空
root_cause: 在数据同步完成前(onSyncFinished之前)调用getConversationListByOption，获取到的会话信息不完整。
solution: 确保在onSyncFinished回调完成后再调用getConversationListByOption获取会话列表，同步完成前获取的信息不完整。
customers: ['海南无限链科技有限公司']
source: chat_history
tags: ['Uniapp', '会话列表', 'teamid', '数据同步', 'onSyncFinished']
created: 2025-01-03
updated: 2026-03-23
---

## 问题：会话名称显示为teamid且头像为空

## 问题详情

**现象**：
偶现会话列表中群聊名称显示为teamid而不是群名称，头像也为空，正常应该显示群名称和群头像。

## 排查过程

1. 客户反馈偶现，非登录前后出现；2. 分析日志发现onSyncStarted开始同步后，在onSyncFinished完成前调用了getConversationListByOption；3. 数据同步完成前查询导致信息不完整。

## 问题原因

在数据同步完成前(onSyncFinished之前)调用getConversationListByOption，获取到的会话信息不完整。

## 解决方案

确保在onSyncFinished回调完成后再调用getConversationListByOption获取会话列表，同步完成前获取的信息不完整。

## 其他触发场景

（合并时在此处追加）
