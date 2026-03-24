---
track_type: 咨询类
sub_type: 接口用法咨询
product: IM-SDK
feature: 聊天室
platform: Uniapp
title: 聊天室linkProvider参数格式要求
root_cause: 
solution: 聊天室linkProvider配置要求：1. 必须返回Promise<Array<string>>类型；2. 正确写法：linkProvider: function(accountId, roomId) { return uni.$nim.V2NIMLoginService.getChatroomLinkAddress(roomId, false) }；3. 若只做聊天室登录（不登录IM），linkProvider里需改为请求服务器API获取地址并返回Promise
customers: ['东莞市云特信息科技有限公司']
source: chat_history
tags: ['聊天室', 'linkProvider', 'Promise', 'Uniapp']
created: 2025-01-07
updated: 2026-03-23
---

## 问题：聊天室linkProvider参数格式要求

## 问题详情

**现象**：
客户配置聊天室linkProvider参数时，不清楚正确的参数格式和返回类型

## 排查过程



## 问题原因



## 解决方案

聊天室linkProvider配置要求：1. 必须返回Promise<Array<string>>类型；2. 正确写法：linkProvider: function(accountId, roomId) { return uni.$nim.V2NIMLoginService.getChatroomLinkAddress(roomId, false) }；3. 若只做聊天室登录（不登录IM），linkProvider里需改为请求服务器API获取地址并返回Promise

## 其他触发场景

（合并时在此处追加）
