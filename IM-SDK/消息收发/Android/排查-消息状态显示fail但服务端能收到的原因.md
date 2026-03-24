---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息收发
platform: Android
title: 消息状态显示fail但服务端能收到的原因
root_cause: 发送方被对方拉黑，客户端消息发送失败状态显示fail，但消息实际上已发送到服务端（抄送可收到）
solution: 服务端需要解析消息抄送中的blacklist字段，通过服务端接口https://doc.yunxin.163.com/messaging/server-apis/DI3OTg5Mjg?platform=server设置拉黑状态
customers: ['积木成林']
source: chat_history
tags: ['消息状态', 'fail', 'blacklist', '拉黑', '消息抄送']
created: 2025-01-03
updated: 2026-03-23
---

## 问题：Android 消息状态显示fail但服务端能收到的原因

## 问题详情

**现象**：
线上用户出现消息message的status显示为fail，但后台能拿到该消息的异常情况。

## 排查过程

1. 客户反馈消息状态显示失败但服务端能收到消息
2. 经排查发现发送方被对方拉黑
3. 消息抄送中有blacklist字段标识
**关键发现**：客户端消息状态显示失败是因为被对方拉黑，但消息实际已发送到服务端

## 问题原因

发送方被对方拉黑，客户端消息发送失败状态显示fail，但消息实际上已发送到服务端（抄送可收到）

## 解决方案

服务端需要解析消息抄送中的blacklist字段，通过服务端接口https://doc.yunxin.163.com/messaging/server-apis/DI3OTg5Mjg?platform=server设置拉黑状态

## 其他触发场景

（合并时在此处追加）
