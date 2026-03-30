---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 推送
platform: iOS
title: Android发送消息iOS端推送不触发拦截回调
root_cause: Android端发送消息时pushPayload缺少apsField层级，需要将mutable-content放到apsField键内
solution: Android端设置pushPayload时，将mutable-content放到apsField键内，参考文档：https://faq.yunxin.163.com/#KB0291
customers: ["微鲤Yaame"]
source: chat_history
tags: ["推送", "iOS", "Android", "mutable-content", "apsField"]
created: 2025-02-24
updated: 2025-03-20
---

## 问题：iOS Android发送消息iOS端推送不触发拦截回调

## 问题详情

**现象**：
iOS给iOS发送IM文本消息，iOS后台收到推送时会走到didReceiveNotificationResponse方法。但Android给iOS发消息，iOS收到推送不走该方法，无法拦截推送。

**环境信息**：
- 平台：iOS
- 涉及：Android端发送、iOS端接收

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 检查iOS端apnsPayload配置 → 需要设置mutable-content
2. 检查Android端payload配置 → 需要设置apsField字段

**关键发现**：Android端缺少apsField层级包装

## 问题原因

Android端发送消息时pushPayload缺少apsField层级，需要将mutable-content放到apsField键内。

## 解决方案

Android端设置pushPayload时，将mutable-content放到apsField键内，参考文档：https://faq.yunxin.163.com/#KB0291

## 其他触发场景
