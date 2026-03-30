---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 聊天室消息
platform: 通用
title: 聊天室自定义消息extension字段客户端读取不到
root_cause: 客户端抄送中extension字段是第三方回调封装的扩展，与消息发送时填充的extension字段是不同概念
solution: 客户端读取聊天室消息extension字段应使用message.toString()方法，或确认抄送消息中extension字段的来源为第三方回调
customers: ["云信+乐次元", "云信-Daily Interactive Entertainment Network Limited"]
source: chat_history
tags: ["聊天室", "extension", "customMessage", "抄送", "message.toString"]
created: 2025-08-04
updated: 2026-03-26
---

## 问题：通用 聊天室自定义消息extension字段客户端读取不到

## 问题详情

**现象**：
聊天室发送自定义消息，消息体中extension字段有值，云端消息记录正常，但客户端收到消息后extension字段读取不到。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
云端消息记录extension字段正常

## 排查过程

1. 确认云端记录消息extension字段正常 → 确认发送时extension有值
2. 检查客户端消息抄送中extension字段 → 发现抄送中extension字段有值
3. 确认为第三方回调的扩展字段，与消息体中的extension不是同一字段 → 定位概念差异

**关键发现**：客户端消息抄送中的extension是第三方回调扩展，与发送时填充的extension不同

## 问题原因

客户端抄送中extension字段是第三方回调封装的扩展，与消息发送时填充的extension字段是不同概念

## 解决方案

客户端读取聊天室消息extension字段应使用message.toString()方法，或确认抄送消息中extension字段的来源为第三方回调。

## 其他触发场景

- [通用] 聊天室自定义消息extension字段客户端读取方法，来源：云信-Daily Interactive Entertainment Network Limited，2026-03-26
