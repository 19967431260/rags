---
track_type: 排查类
sub_type: 使用问题
product: 呼叫组件
feature: 音视频通话
platform: 安卓
title: accept2返回-1且通话自动挂断
root_cause: 在接听前对呼叫发送了busy回复，导致chatId被移除，info为null
solution: 检查业务逻辑，避免在接听前发送busy回复；如已发送busy则无法接听该呼叫
customers: ["北京奥腾环球信息咨询有限责任公司"]
source: chat_history
tags: ["呼叫组件", "accept2", "busy", "自动挂断"]
created: 2025-06-03
updated: 2025-03-23
---

## 问题：安卓 accept2返回-1且通话自动挂断

## 问题详情

**现象**：
接听呼叫时accept2返回-1，且接听后通话自动挂断。日志显示accept2和hangUp2几乎同时调用。

## 排查过程

1. 分析日志发现accept2和hangUp2几乎同时调用
2. 发现调用accept2为-1是因为之前对该呼叫发送了busy回复
3. 检查chatId被移除的原因 → 发送了busy导致info为null

**关键发现**：在接听前对呼叫发送了busy回复，导致chatId被移除，info为null

## 问题原因

在接听前对呼叫发送了busy回复，导致chatId被移除，info为null

## 解决方案

检查业务逻辑，避免在接听前发送busy回复；如已发送busy则无法接听该呼叫

## 其他触发场景

