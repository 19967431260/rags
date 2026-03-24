---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 房间回调
platform: Uniapp
title: onUserJoined回调未触发问题
root_cause: B用户实际未成功加入房间(403错误)，所以双方都没有收到对方加入的回调
solution: 1. 确保双方使用相同的channelName
2. 检查鉴权token是否正确
3. 确认加入房间成功后才会触发onUserJoined
4. 双方都会收到房间内其他用户的回调
customers: ['重庆简房科技']
source: chat_history
tags: ['onUserJoined', '回调', '加入房间', 'Uniapp']
created: 2025-01-03
updated: 2026-03-23
---

## 问题：onUserJoined回调未触发问题

## 问题详情

**现象**：
A用户创建并加入房间，B用户加入时A端未触发onUserJoined回调。

## 排查过程

1. 检查B用户加入时的回调
2. 发现只返回了自己的userID
3. 检查日志发现加入房间403失败

## 问题原因

B用户实际未成功加入房间(403错误)，所以双方都没有收到对方加入的回调

## 解决方案

1. 确保双方使用相同的channelName
2. 检查鉴权token是否正确
3. 确认加入房间成功后才会触发onUserJoined
4. 双方都会收到房间内其他用户的回调

## 其他触发场景

（合并时在此处追加）
