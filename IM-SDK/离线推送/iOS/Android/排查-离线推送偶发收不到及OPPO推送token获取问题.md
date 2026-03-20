---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 离线推送
platform: iOS/Android
title: 离线推送偶发收不到及OPPO推送token获取问题
root_cause: 1. 用户在线时消息直接下发无推送通知；2. OPPO推送配置问题导致token获取失败
solution: 1. 区分在线下发和离线推送场景；2. 使用HeytapPushManager.register调试OPPO推送配置，参考官方文档：https://open.oppomobile.com/documentation/page/info?id=11224
customers: ["杭州跨客技术服务有限公司"]
source: chat_history
tags: ["离线推送", "OPPO推送", "token获取", "iOS推送"]
created: 2025-10-31
updated: 2026-03-20
---

## 问题：iOS/Android 离线推送偶发收不到及OPPO推送token获取问题

## 问题详情

**现象**：
客户反馈iOS端偶尔收不到离线推送通知，以及OPPO推送token无法获取的问题。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客户反馈离线推送偶发收不到
2. 检查发现用户在线时下发消息不走离线推送
3. OPPO推送token获取返回code-2
4. 建议参考OPPO官方文档检查配置

**关键发现**：

## 问题原因

1. 用户在线时消息直接下发无推送通知；2. OPPO推送配置问题导致token获取失败

## 解决方案

1. 区分在线下发和离线推送场景；2. 使用HeytapPushManager.register调试OPPO推送配置，参考官方文档：https://open.oppomobile.com/documentation/page/info?id=11224

## 其他触发场景

