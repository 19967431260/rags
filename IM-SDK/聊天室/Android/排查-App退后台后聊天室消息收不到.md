---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 聊天室
platform: Android
title: App退后台后聊天室消息收不到
root_cause: App退后台后，系统限制网络传输，长连接断开，导致无法收到在线聊天室消息
solution: IM消息可以走推送，聊天室消息目前无法推送，只能重新登录后获取云端历史消息。
customers:
  - 湖北盛天
source: chat_history
tags:
  - 聊天室
  - 后台
  - 消息收不到
  - 网络限制
  - Android
created: '2025-06-26'
updated: '2025-03-23'
---

## 问题：Android App退后台后聊天室消息收不到

## 问题详情

**现象**：
App退到后台一段时间后，聊天室的消息收不到，回到前台才能接收消息。应用进程未被系统回收。

**排查过程**：

1. 查看日志发现退后台4s后网络被系统限制
2. 报错：java.io.IOException: Software caused connection abort
3. 确认是系统限制后台网络传输

**关键发现**：App退后台后，系统限制网络传输，长连接断开，导致无法收到在线聊天室消息

## 问题原因

App退后台后，系统限制网络传输，长连接断开，导致无法收到在线聊天室消息

## 解决方案

IM消息可以走推送，聊天室消息目前无法推送，只能重新登录后获取云端历史消息。
