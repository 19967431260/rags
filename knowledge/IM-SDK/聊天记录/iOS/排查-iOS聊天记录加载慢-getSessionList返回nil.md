---
track_type: 排查类
sub_type: 线上事故
product: IM-SDK
feature: 聊天记录
platform: iOS
title: iOS聊天记录加载慢-getSessionList返回nil
root_cause: 问题时间点日志已缺失，无法确定具体原因。
solution: 需要等下次问题出现时及时拉取日志分析。
customers: ['深圳岸涌']
source: chat_history
tags: ['iOS', 'getSessionList', '返回nil', '聊天记录', '加载慢']
created: 2025-01-10
updated: 2026-03-23
---

## 问题：iOS iOS聊天记录加载慢-getSessionList返回nil

## 问题详情

**现象**：
线上用户反馈会话列表有收到消息，点进聊天页面查不出来，需要等1分钟左右才显示。iOS端偶现getSessionList返回nil。

## 排查过程

1. 客户反馈线上用户会话列表显示收到消息，但聊天记录第一时间没查出来
2. 询问是否有报错码，客户反馈没有报错就是慢
3. 另一客户反馈iOS之前也出现过getSessionList返回nil的情况
4. 技术支持要求提供视频、会话ID和用户accid结合日志分析
5. 客户发送视频和相关信息
6. 技术支持拉取日志后发现只有11点之后的日志，视频中是10点半左右的问题

## 问题原因

问题时间点日志已缺失，无法确定具体原因。

## 解决方案

需要等下次问题出现时及时拉取日志分析。

## 其他触发场景

（合并时在此处追加）
