---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息发送
platform: 小程序
title: Uniapp小程序发送语音消息size类型错误
root_cause: Uniapp小程序SDK发送语音消息时，size参数类型传为字符串而非数字。
solution: 临时方案：第三方回调接口兼容处理string和number类型的size字段。内部已确认问题并协调修复。
customers: ["杭州顺网科技"]
source: chat_history
tags: ["小程序", "语音消息", "size类型", "第三方回调", "Uniapp"]
created: 2025-05-22
updated: 2025-03-20
---

## 问题：小程序 Uniapp小程序发送语音消息size类型错误

## 问题详情

**现象**：
Uniapp小程序发送语音消息时，第三方回调收到size字段类型为字符串而非数字，导致消息被拦截。SDK版本0.17.1和0.19.2均有此问题。

**环境信息**：
- SDK 版本：
- 系统版本 / 设备：
- 平台：小程序

## 排查过程

1. 客户反馈发送语音消息返回403无权限错误 → 技术支持发现第三方回调拒绝
2. 对比正常消息和异常消息的回调参数 → 发现size字段类型不一致（string vs number）
3. 确认为小程序SDK传参问题，建议客户临时兼容处理

## 问题原因

Uniapp小程序SDK发送语音消息时，size参数类型传为字符串而非数字。

## 解决方案

临时方案：第三方回调接口兼容处理string和number类型的size字段。内部已确认问题并协调修复。

## 其他触发场景

