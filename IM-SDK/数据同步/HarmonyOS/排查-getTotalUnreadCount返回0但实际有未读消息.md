---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 数据同步
platform: HarmonyOS
title: getTotalUnreadCount返回0但实际有未读消息
root_cause: IM SDK登录后会自动进行数据同步，如果在同步完成前调用查询接口，可能无法获取到完整数据。
solution: IM SDK登录后会自动进行数据同步，建议在收到onSyncFinished回调后再调用getTotalUnreadCount等接口查询数据。
customers: ['联通在线信息科技有限公司']
source: chat_history
tags: ['HarmonyOS', '数据同步', 'getTotalUnreadCount', 'onSyncFinished', '未读消息']
created: 2025-01-15
updated: 2026-03-23
---

## 问题：HarmonyOS getTotalUnreadCount返回0但实际有未读消息

## 问题详情

**现象**：
实例化IM后调用conversationService.getTotalUnreadCount返回0，但实际有未读消息数。

## 排查过程

1. 确认是否在数据同步完成后调用接口 → 客户未关注同步状态
2. 建议监听onSyncFinished事件后再调用接口
3. 客户验证：加定时1秒后调用可以获取到值

## 问题原因

IM SDK登录后会自动进行数据同步，如果在同步完成前调用查询接口，可能无法获取到完整数据。

## 解决方案

IM SDK登录后会自动进行数据同步，建议在收到onSyncFinished回调后再调用getTotalUnreadCount等接口查询数据。

## 其他触发场景

（合并时在此处追加）
