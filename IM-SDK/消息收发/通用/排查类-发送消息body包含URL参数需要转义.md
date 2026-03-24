---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息收发
platform: 通用
title: 发送消息body包含URL参数需要转义
root_cause: 消息body中包含未转义的URL参数&符号，导致JSON解析失败
solution: 发送消息时如果body中包含URL且URL带有参数（含&符号），需要对URL进行转义处理。例如将&替换为%26，确保body是合法的JSON格式。
customers: ['深圳宸瑞麟科技技术对接群']
source: chat_history
tags: ['IM-SDK', '服务端API', '414', 'body-not-json', 'URL转义']
created: 2024-12-31
updated: 2026-03-23
---

## 问题：发送消息body包含URL参数需要转义

## 问题详情

**现象**：
客户在使用服务端API发送消息时，如果消息body中包含URL且该URL带有&参数，会返回414错误码，提示body-not-json。

## 排查过程

1. 客户发送消息时返回414错误
2. 客户发现消息内容包含带&的URL参数
3. 技术支持确认需要对URL中的&进行转义

## 问题原因

消息body中包含未转义的URL参数&符号，导致JSON解析失败

## 解决方案

发送消息时如果body中包含URL且URL带有参数（含&符号），需要对URL进行转义处理。例如将&替换为%26，确保body是合法的JSON格式。

## 其他触发场景

（合并时在此处追加）
