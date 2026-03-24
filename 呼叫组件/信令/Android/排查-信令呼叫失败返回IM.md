---
track_type: 排查类
sub_type: 使用问题
product: 呼叫组件
feature: 信令
platform: Android
title: 信令呼叫失败返回IM code 414
root_cause: 接收方accid不存在或格式错误（云信accid均为小写）
solution: 检查接收方accid是否在当前appkey下注册，确保accid为小写格式
customers: ["山东中时通"]
source: chat_history
tags: ["414", "信令", "accid", "参数错误"]
created: 2025-02-17
updated: 2026-03-20
---

## 问题：Android 信令呼叫失败返回IM code 414

## 问题详情

**现象**：
音视频通话发起失败，signal call failed with im code 414，仅特定客户出现。

## 排查过程

1. 分析错误码 → 414表示参数错误
2. 检查IM日志 → 发现接收方accid不存在
3. 确认账号格式 → 云信accid都是小写，客户提供的accid格式有误

## 问题原因

接收方accid不存在或格式错误（云信accid均为小写）

## 解决方案

检查接收方accid是否在当前appkey下注册，确保accid为小写格式

## 其他触发场景

