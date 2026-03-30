---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 自定义消息
platform: Server
title: 聊天室CUSTOM消息attach字段为空
root_cause: 服务端发送CUSTOM消息时attach字段直接传字符串，客户端无法正确解析
solution: 发送CUSTOM消息时，attach字段需要传入JSON格式内容，参考文档：https://doc.yunxin.163.com/messaging/server-apis/DQ2NTg4ODE?platform=server
customers: ['VIP云信-北京沃德博创信息']
source: chat_history
tags: ['IM', '聊天室', 'CUSTOM', 'attach', '服务端']
created: 2025-01-21
updated: 2026-03-23
---

## 问题：Server 聊天室CUSTOM消息attach字段为空

## 问题详情

**现象**：
通过服务端接口发送聊天室CUSTOM消息，移动端接收到的消息中attach字段信息丢失。

## 排查过程

1. 客户反馈attach字段为空。
2. 查看服务端发送参数，发现attach直接传了字符串。
3. 建议将attach内容包装为JSON格式。

## 问题原因

服务端发送CUSTOM消息时attach字段直接传字符串，客户端无法正确解析

## 解决方案

发送CUSTOM消息时，attach字段需要传入JSON格式内容，参考文档：https://doc.yunxin.163.com/messaging/server-apis/DQ2NTg4ODE?platform=server

## 其他触发场景

（合并时在此处追加）
