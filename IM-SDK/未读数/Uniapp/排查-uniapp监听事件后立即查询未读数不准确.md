---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 未读数
platform: Uniapp
title: uniapp监听事件后立即查询未读数不准确
root_cause: SDK内部异步处理机制，事件触发时数据尚未完成更新，主动查询时机不对导致读到的是上一状态
solution: 总未读数通过onTotalUnreadCountChanged事件获取，不要主动查询；好友申请未读数首次调用getAddApplicationUnreadCount后，在内存中维护UnreadCount并根据事件+1修正；会话列表根据事件驱动处理而非主动查询
customers: ["上海文攸网络科技有限公司","芜湖市乖巧虎科技有限公司"]
source: chat_history
tags: ["onReceiveMessages","getTotalUnreadCount","Uniapp","异步","事件监听"]
created: 2025-08-05
updated: 2026-03-26
---

## 问题：Uniapp uniapp监听事件后立即查询未读数不准确

## 问题详情

**现象**：
uniapp SDK监听onReceiveMessages和onFriendAddApplication事件后，立即调用getTotalUnreadCount、getAddApplicationUnreadCount或getConversationList，读取到的数据是旧的（差1），延迟1ms后读取才正确。

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

**关键发现**：SDK内部异步处理机制，事件触发时数据尚未完成更新，主动查询时机不对导致读到的是上一状态

## 问题原因

SDK内部异步处理机制，事件触发时数据尚未完成更新，主动查询时机不对导致读到的是上一状态。

## 解决方案

总未读数通过onTotalUnreadCountChanged事件获取，不要主动查询；好友申请未读数首次调用getAddApplicationUnreadCount后，在内存中维护UnreadCount并根据事件+1修正；会话列表根据事件驱动处理而非主动查询。

## 其他触发场景

（合并时在此处追加）
