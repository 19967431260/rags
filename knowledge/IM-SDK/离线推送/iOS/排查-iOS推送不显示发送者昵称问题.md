---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 离线推送
platform: iOS
title: iOS推送不显示发送者昵称问题
root_cause: payload中设置了apsField.alert.body字段时，iOS推送会使用apsField中的内容，不会根据needPushNick决定是否携带用户昵称
solution: 去掉apsField.alert设置，或不设置pushTitle，让推送内容根据needPushNick自动携带昵称；如需自定义标题，需自行在pushcontent中拼接发送者昵称
customers: ['北京创新一号']
source: chat_history
tags: ['iOS推送', 'needPushNick', 'apsField', '推送昵称', 'payload']
created: 2025-01-16
updated: 2026-03-23
---

## 问题：iOS iOS推送不显示发送者昵称问题

## 问题详情

**现象**：
客户使用服务端API发送P2P消息，设置needPushNick=true，安卓端推送显示昵称，iOS端不显示。

## 排查过程

1. 检查参数设置 → 确认needPushNick=true已设置
2. 对比Postman测试 → Postman发送正常，iOS有昵称
3. 检查payload参数 → 发现设置了apsField.alert.body
4. 关键发现：apsField优先级高于needPushNick，设置了apsField后推送内容不会根据needPushNick携带昵称

## 问题原因

payload中设置了apsField.alert.body字段时，iOS推送会使用apsField中的内容，不会根据needPushNick决定是否携带用户昵称

## 解决方案

去掉apsField.alert设置，或不设置pushTitle，让推送内容根据needPushNick自动携带昵称；如需自定义标题，需自行在pushcontent中拼接发送者昵称

## 其他触发场景

（合并时在此处追加）
