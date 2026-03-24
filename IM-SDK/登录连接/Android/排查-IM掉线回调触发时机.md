---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 登录连接
platform: Android
title: IM掉线回调触发时机
root_cause: SDK判断掉线后会触发回调。如果网络状态不好（非直接断开），可能存在心跳检测延迟
solution: 监听onConnectStatus回调获取连接状态变化。如问题持续，提供SDK日志和具体时间进行排查
customers: ['VIP云信-邯郸市趣网传媒技术有限公司']
source: chat_history
tags: ['onDisconnected', '掉线回调', 'onConnectStatus', 'Android']
created: 2025-01-20
updated: 2026-03-23
---

## 问题：Android IM掉线回调触发时机

## 问题详情

**现象**：
onDisconnected链接断开的回调在重新连上时才收到，希望在断开时立即收到回调

## 排查过程

1. 确认网络断开时回调是否触发 → 直接断开会收到回调
2. 分析网络状态不好导致的问题 → 不是直接断开，偶现收不到消息
3. 建议检查SDK日志确认状态

## 问题原因

SDK判断掉线后会触发回调。如果网络状态不好（非直接断开），可能存在心跳检测延迟

## 解决方案

监听onConnectStatus回调获取连接状态变化。如问题持续，提供SDK日志和具体时间进行排查

## 其他触发场景

（合并时在此处追加）
