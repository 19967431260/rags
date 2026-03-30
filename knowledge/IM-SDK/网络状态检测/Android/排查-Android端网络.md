---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 网络状态检测
platform: Android
title: Android端网络异常时SDK重连机制及回调说明
root_cause: 系统未给SDK断网回调，SDK只能通过心跳检测或发包失败感知网络异常
solution: 断网期间如用户未发消息，SDK需等待下次心跳检测才能感知网络异常。可关注onConnectStatus、onDisconnected、onConnectFailed回调获取连接状态变化。心跳间隔时间可通过SDK配置调整。
customers: ["邯郸市趣网传媒技术有限公司"]
source: chat_history
tags: ["网络异常", "重连", "心跳检测", "onConnectStatus", "Android"]
created: 2025-02-13
updated: 2026-03-20
---

## 问题：Android Android端网络异常时SDK重连机制及回调说明

## 问题详情

**现象**：
客户反馈2025-02-13 14:50-14:54期间收不到消息，SDK日志显示网络异常且一直在重试。

## 排查过程

1. 分析日志 → 发现网络异常，SDK一直在重试，reader idle timeout
2. 确认断网感知时机 → 系统未给SDK断网回调，SDK无法第一时间感知
3. 确认恢复机制 → SDK通过心跳检测发现网络问题后开始重连
4. 确认回调触发 → 心跳检测失败后触发onConnectStatus/onDisconnected/onConnectFailed回调

## 问题原因

系统未给SDK断网回调，SDK只能通过心跳检测或发包失败感知网络异常

## 解决方案

断网期间如用户未发消息，SDK需等待下次心跳检测才能感知网络异常。可关注onConnectStatus、onDisconnected、onConnectFailed回调获取连接状态变化。心跳间隔时间可通过SDK配置调整。

## 其他触发场景
- [Android] Android端网络异常时SDK重连机制及回调说明，来源：['邯郸市趣网传媒技术有限公司']，2026-03-20
- [Android] Android端网络异常时SDK重连机制及回调说明，来源：['邯郸市趣网传媒技术有限公司']，2026-03-20

