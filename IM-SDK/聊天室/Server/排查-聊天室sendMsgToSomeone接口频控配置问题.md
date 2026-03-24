---
track_type: 排查类
sub_type: 配置开通咨询
product: IM-SDK
feature: 聊天室
platform: Server
title: 聊天室sendMsgToSomeone接口频控配置问题
root_cause: /chatroom/sendMsgToSomeone.action和/chatroom/sendMsg.action的频控配置不一致，前者默认为1秒100次
solution: 调整/chatroom/sendMsgToSomeone.action接口频控配置为1000次/秒，与/chatroom/sendMsg.action保持一致
customers: ['新视展-印度社交app']
source: chat_history
tags: ['聊天室', '频控', 'sendMsgToSomeone', 'query too fast']
created: 2025-02-19
updated: 2026-03-23
---

## 问题：Server 聊天室sendMsgToSomeone接口频控配置问题

## 问题详情

**现象**：
频控已调到1000，但/chatroom/sendMsgToSomeone.action接口仍返回query too fast，而/chatroom/sendMsg.action正常

**环境信息**：
- 平台：Server
- 产品：IM-SDK

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客户提供appkey和错误截图 → 技术支持查询接口调用情况
2. 发现sendMsgToSomeone.action超过1秒100次限制
3. 确认两个接口频控配置不一致
4. 调整sendMsgToSomeone.action配置与sendMsg.action一致为1000次/秒

## 问题原因

/chatroom/sendMsgToSomeone.action和/chatroom/sendMsg.action的频控配置不一致，前者默认为1秒100次

## 解决方案

调整/chatroom/sendMsgToSomeone.action接口频控配置为1000次/秒，与/chatroom/sendMsg.action保持一致

## 其他触发场景

（合并时在此处追加：`- [Server] 聊天室sendMsgToSomeone接口频控配置问题，来源：['新视展-印度社交app']，2026-03-23`）
