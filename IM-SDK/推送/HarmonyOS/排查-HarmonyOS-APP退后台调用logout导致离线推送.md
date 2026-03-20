---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 推送
platform: HarmonyOS
title: APP退后台调用logout导致离线推送收不到
root_cause: APP退后台后调用了logout接口，导致推送token被解绑，离线消息无法通过推送送达。
solution: APP退后台时不需要调用logout，保持登录状态才能接收离线推送。如需切换账号，应在切换时调用logout，而非退后台时。
customers: ["FVIP-云信-上海麦色"]
source: chat_history
tags: ["HarmonyOS", "离线推送", "logout", "推送token", "退后台"]
created: 2025-11-18
updated: 2026-03-20
---

## 问题：HarmonyOS APP退后台调用logout导致离线推送收不到

## 问题详情

**现象**：
鸿蒙设备作为消息接收方，APP被杀后离线推送收不到。客户误以为需要在payload中配置harmonyField的token参数。

## 排查过程

1. 检查推送配置 → 客户询问harmonyField的token如何获取
2. 查看接收端日志 → 发现APP退后台后直接调用了logout接口
**关键发现**：调用logout会解绑推送token，导致离线推送无法送达

## 问题原因

APP退后台后调用了logout接口，导致推送token被解绑，离线消息无法通过推送送达。

## 解决方案

APP退后台时不需要调用logout，保持登录状态才能接收离线推送。如需切换账号，应在切换时调用logout，而非退后台时。

## 其他触发场景

