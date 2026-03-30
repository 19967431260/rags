---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 聊天室消息
platform: Web
title: 聊天室成员头像含非法字符导致getChatroomMembers报错
root_cause: 聊天室成员头像URL包含特殊字符，不能被decodeURIComponent解析，导致SDK内部解析报错
solution: 头像URL在设置前先进行encodeURIComponent编码，防止特殊字符导致解析失败
customers:
  - 湖南腾速科技
source: chat_history
tags:
  - IM
  - Web
  - 聊天室
  - URI malformed
  - 头像
  - decodeURIComponent
created: '2025-06-19'
updated: '2025-03-23'
---

## 问题：Web 聊天室成员头像含非法字符导致getChatroomMembers报错

## 问题详情

**现象**：
Web端调用chatroom.getChatroomMembers接口不返回数据，控制台报错URI malformed。仅特定聊天室出现问题，其他聊天室正常。

**排查过程**：

1. 客户反馈特定聊天室获取成员列表无返回
2. 查看控制台日志 → 发现URI malformed错误
3. 分析错误堆栈 → decodeURIComponent解析头像时失败
4. 确认聊天室某成员头像URL包含非法字符

**关键发现**：聊天室成员头像URL包含特殊字符，不能被decodeURIComponent解析，导致SDK内部解析报错

## 问题原因

聊天室成员头像URL包含特殊字符，不能被decodeURIComponent解析，导致SDK内部解析报错

## 解决方案

头像URL在设置前先进行encodeURIComponent编码，防止特殊字符导致解析失败
