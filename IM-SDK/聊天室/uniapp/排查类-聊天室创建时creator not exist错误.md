---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 聊天室
platform: Uniapp
title: 聊天室创建时creator not exist错误
root_cause: 创建聊天室的creator参数需要传入已创建好的IM账号（accid），不是手机号或其他平台账号
solution: 创建聊天室时，creator参数应传入已注册的IM账号accid，不是手机号。聊天室创建后控制台没有列表展示，需要业务侧自行维护，或通过服务端API根据创建者账号查询。关闭聊天室相当于删除，可以重新开放
customers: ['东莞市云特信息科技有限公司']
source: chat_history
tags: ['聊天室', '创建', 'creator', 'Uniapp']
created: 2025-01-07
updated: 2026-03-23
---

## 问题：聊天室创建时creator not exist错误

## 问题详情

**现象**：
客户创建聊天室时提示creator not exist错误，不清楚creator应该传什么值

## 排查过程



## 问题原因

创建聊天室的creator参数需要传入已创建好的IM账号（accid），不是手机号或其他平台账号

## 解决方案

创建聊天室时，creator参数应传入已注册的IM账号accid，不是手机号。聊天室创建后控制台没有列表展示，需要业务侧自行维护，或通过服务端API根据创建者账号查询。关闭聊天室相当于删除，可以重新开放

## 其他触发场景

（合并时在此处追加）
