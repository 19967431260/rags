---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 登录
platform: iOS
title: iOS端logout后仍收到推送的排查
root_cause: 可能原因：1. 同一设备登录了多个账号，其他账号仍在收取推送；2. Flutter SDK的logout回调未正确触发登出协议上报。
solution: 1. 使用点对点消息而非群消息测试验证是否真的在登出后仍收到推送；2. 确认同一设备上是否只有要测试的账号登录；3. 检查Flutter代码中logout后登录状态是否正确变化；4. 如果确认logout已调用但协议未上报，建议检查Flutter SDK版本或提供复现日志
customers: ["西安潮玩时代网络科技有"]
source: chat_history
tags: ["logout", "推送", "APNS", "iOS", "Flutter"]
created: 2025-08-12
updated: 2026-03-26
---

## 问题：iOS iOS端logout后仍收到推送的排查

## 问题详情

**现象**：
iOS端Flutter集成云信SDK，登出账号后手机仍能收到推送通知。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：iOS
- 其他：Flutter集成

**相关日志**：
服务端查询不到logout协议上报

## 排查过程

1. 客服确认登出后会清除推送token → 确认SDK应该清除token
2. 建议检查是否同一设备上有其他accid未登出 → 考虑多账号场景
3. 如果都在同一个群里，会误以为登出账号收到了推送 → 群消息误判
4. 客服在服务端查询该accid的登出协议记录，未找到 → 确认协议未上报
5. 使用点对点消息测试验证 → 确认真实场景

**关键发现**：服务端查询不到logout协议上报，但客户确认调用了logout

## 问题原因

可能原因：1. 同一设备登录了多个账号，其他账号仍在收取推送；2. Flutter SDK的logout回调未正确触发登出协议上报。

## 解决方案

1. 使用点对点消息而非群消息测试验证是否真的在登出后仍收到推送
2. 确认同一设备上是否只有要测试的账号登录
3. 检查Flutter代码中logout后登录状态是否正确变化
4. 如果确认logout已调用但协议未上报，建议检查Flutter SDK版本或提供复现日志

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
