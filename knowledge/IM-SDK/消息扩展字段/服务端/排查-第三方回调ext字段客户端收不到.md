---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息扩展字段
platform: 服务端
title: 第三方回调ext字段客户端收不到
root_cause: 客户端混淆了callbackExt和remoteExt字段
solution: 客户端通过remoteExt获取回调中的ext字段；如需扩展callbackExt长度可付费调整至5k
customers: ['南京寻优']
source: chat_history
tags: ['第三方回调', 'ext', 'remoteExt', 'callbackExt', 'IM']
created: 2025-01-06
updated: 2026-03-23
---

## 问题：服务端 第三方回调ext字段客户端收不到

## 问题详情

**现象**：
客户在第三方回调中增加了ext字段，但客户端收不到。原因是客户端需要通过remoteExt获取，且callbackExt和remoteExt是不同的字段。

## 排查过程

1. 客户反馈ext字段客户端收不到 → 客服检查发现服务端确实塞了ext
2. 确认callbackExt和remoteExt都塞了相同内容
3. 客户发现callbackExt在字符过多时不显示
4. 确认remoteExt就是客户发的ext内容

## 问题原因

客户端混淆了callbackExt和remoteExt字段

## 解决方案

客户端通过remoteExt获取回调中的ext字段；如需扩展callbackExt长度可付费调整至5k

## 其他触发场景

（合并时在此处追加）
