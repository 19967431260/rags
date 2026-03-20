---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息发送
platform: Server
title: 服务端回调响应扩展参数客户端读取不到
root_cause: response code非200时无法读取扩展参数
solution: 确保服务端回调返回response code为200，客户端才能读取ext内容。拦截与否取决于errCode，与responseCode无关。
customers: ["东莞市面具网络科技有限公司"]
source: chat_history
tags: ["服务端回调", "扩展参数", "response code", "消息拦截"]
created: 2025-11-19
updated: 2026-03-20
---

## 问题：Server 服务端回调响应扩展参数客户端读取不到

## 问题详情

**现象**：
客户在服务端回调响应接口里加了扩展参数，客户端SDK读取不到。

**排查过程**：
1. 检查客户端读取代码
2. 发现response code是20001而非200
3. 确认只有response code为200时才能读取ext内容

## 问题原因

response code非200时无法读取扩展参数

## 解决方案

确保服务端回调返回response code为200，客户端才能读取ext内容。拦截与否取决于errCode，与responseCode无关。
