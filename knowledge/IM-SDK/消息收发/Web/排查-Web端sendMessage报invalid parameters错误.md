---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息收发
platform: Web
title: Web端sendMessage报invalid parameters错误
root_cause: sendMessage接口调用参数错误,传入了多余的参数或参数格式不正确
solution: sendMessage只需传2个参数: await nim.V2NIMMessageService.sendMessage(message, 'conversationId'),其中conversationId是字符串格式如'test1|1|test2'
customers: ["山西云钢智造网络科技"]
source: chat_history
tags: ["invalid parameters", "sendMessage", "Web", "参数错误"]
created: 2026-02-02
updated: 2026-03-17
---

## 问题：Web Web端sendMessage报invalid parameters错误

## 问题详情

**现象**：
Web端调用sendMessage发送消息时报错"invalid parameters",发送消息参数错误。

## 排查过程

1. 检查sendMessage调用代码 → 发现传入了3个参数
2. 确认正确用法 → sendMessage只需传2个参数:message对象和conversationId字符串

**关键发现**: 用户错误地将conversationId作为对象传入了第三个参数位置

## 问题原因

sendMessage接口调用参数错误,传入了多余的参数或参数格式不正确

## 解决方案

sendMessage只需传2个参数: await nim.V2NIMMessageService.sendMessage(message, 'conversationId'),其中conversationId是字符串格式如'test1|1|test2'

## 其他触发场景

（暂无）
