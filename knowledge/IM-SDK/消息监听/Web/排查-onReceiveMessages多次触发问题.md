---
track_type: 排查类
sub_type: 功能异常
product: IM-SDK
feature: 消息监听
platform: Web
title: onReceiveMessages多次触发问题
root_cause: 注册了多次监听导致
solution: 该问题通常是因为注册了多次监听导致的。建议检查监听注册逻辑，确保只注册一次。可以使用空工程测试验证。如果问题偶现，尝试强制刷新页面(ctrl+F5)清除缓存。
customers: ["重庆橙心物流网络"]
source: chat_history
tags: ["onReceiveMessages", "多次触发", "消息监听", "Web"]
created: 2025-05-06
updated: 2025-03-23
---

## 问题：Web onReceiveMessages多次触发问题

## 问题详情

**现象**：
一对一聊天收到新消息时，onReceiveMessages监听触发多次。

**环境信息**：
- 平台：Web

## 排查过程

**关键发现**：注册了多次监听

## 问题原因

注册了多次监听导致

## 解决方案

该问题通常是因为注册了多次监听导致的。建议检查监听注册逻辑，确保只注册一次。可以使用空工程测试验证。如果问题偶现，尝试强制刷新页面(ctrl+F5)清除缓存。
