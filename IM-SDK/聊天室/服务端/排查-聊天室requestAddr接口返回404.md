---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 聊天室
platform: 服务端
title: 聊天室requestAddr接口返回404
root_cause: 聊天室不存在或已被删除
solution: 检查roomId是否正确，确认聊天室是否存在。
customers: ['AB Leisure Exponent Inc']
source: chat_history
tags: ['聊天室', 'requestAddr', '404', 'roomId']
created: 2025-01-17
updated: 2026-03-23
---

## 问题：服务端 聊天室requestAddr接口返回404

## 问题详情

**现象**：
调用/nimserver/chatroom/requestAddr.action接口返回code 404，使用域名https://api-sg.netease.im。

## 排查过程

1. 客户反馈接口返回404 → 技术支持询问appkey → 客户提供appkey → 技术支持查询 → 确认聊天室不存在

## 问题原因

聊天室不存在或已被删除

## 解决方案

检查roomId是否正确，确认聊天室是否存在。

## 其他触发场景

（合并时在此处追加）
