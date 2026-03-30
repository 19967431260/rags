---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 推送
platform: Android
title: FCM推送消息收不到排查
root_cause: FCM推送格式中channel_id字段层级错误，应放在android.notification下而非message.notification下。
solution: 调整fcmFieldV1中channel_id字段层级到android.notification下，与importance同层级。
customers: ['深圳市视泰科技有限公司']
source: chat_history
tags: ['FCM', '推送', 'Android', 'channel_id']
created: 2025-02-19
updated: 2026-03-23
---

## 问题：Android FCM推送消息收不到排查

## 问题详情

**现象**：
Android端使用服务端API发送自定义系统通知，前台能收到消息，退出后谷歌FCM推送收不到。

**环境信息**：
- 平台：Android
- 产品：IM-SDK

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 检查推送token → 获取正常
2. 查看推送日志 → 显示推送成功
3. 对比谷歌后台推送 → 谷歌后台推送正常
4. 检查payload格式 → 发现channel_id字段位置错误

## 问题原因

FCM推送格式中channel_id字段层级错误，应放在android.notification下而非message.notification下。

## 解决方案

调整fcmFieldV1中channel_id字段层级到android.notification下，与importance同层级。

## 其他触发场景

（合并时在此处追加：`- [Android] FCM推送消息收不到排查，来源：['深圳市视泰科技有限公司']，2026-03-23`）
