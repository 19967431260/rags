---
track_type: 排查类
sub_type: 使用问题
product: IM-UIKit
feature: 聊天记录
platform: Android
title: Android清空聊天记录后页面未刷新
root_cause: 清空操作后仅清除了数据，但未通知UI层刷新消息列表。
solution: 在清理回调中通知ChatBaseFragment调用chatView.getMessageListView().clearMessageList()刷新UI。可通过LiveData实现，如updateMessageLiveData传空值，在ChatBaseFragment监听后调用clearMessageList。
customers: ['VIP云信-沈阳捷影']
source: chat_history
tags: ['清空聊天记录', '页面刷新', 'UIKit', 'Android', 'clearHistoryMessage']
created: 2025-02-20
updated: 2026-03-23
---

## 问题：Android Android清空聊天记录后页面未刷新

## 问题详情

**现象**：
Android V10 UIKit(10.3.2)调用clearHistoryMessage清空聊天记录后，聊天页面消息列表未刷新，仍有缓存数据。

**环境信息**：
- 平台：Android
- 产品：IM-UIKit

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 确认是自定义添加的清空功能
2. 检查清理回调触发情况 → 回调可正常触发
3. 需要通知ChatBaseFragment刷新UI

## 问题原因

清空操作后仅清除了数据，但未通知UI层刷新消息列表。

## 解决方案

在清理回调中通知ChatBaseFragment调用chatView.getMessageListView().clearMessageList()刷新UI。可通过LiveData实现，如updateMessageLiveData传空值，在ChatBaseFragment监听后调用clearMessageList。

## 其他触发场景

（合并时在此处追加：`- [Android] Android清空聊天记录后页面未刷新，来源：['VIP云信-沈阳捷影']，2026-03-23`）
