---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 房间管理
platform: 服务端
title: RTC服务端创建房间cid与channelId区别
root_cause: 客户端加入房间时应使用创建时传入的channelName字符串，而非使用服务端返回的cid。
solution: 创建房间时使用channelName（字符串）作为参数，客户端加入房间时也要使用相同的channelName字符串。cid是创建成功返回的房间唯一标识（long类型），不用于加入房间。
customers: ['良医健康医疗科技(辽宁)有限公司']
source: chat_history
tags: ['RTC', '服务端', '创建房间', 'cid', 'channelName', 'channelId']
created: 2025-01-06
updated: 2026-03-23
---

## 问题：服务端 RTC服务端创建房间cid与channelId区别

## 问题详情

**现象**：
使用服务端接口创建房间返回cid，但消息通知中房间号在channelName字段，channelId又是什么。

## 排查过程

1. 确认创建房间参数 → 使用channelName=房间1736132916308创建
2. 分析客户端入参 → 发现客户端使用服务端返回的cid作为加入房间参数
3. 明确字段含义 → cid是创建成功返回的long类型ID，channelName是创建时传入的string参数

## 问题原因

客户端加入房间时应使用创建时传入的channelName字符串，而非使用服务端返回的cid。

## 解决方案

创建房间时使用channelName（字符串）作为参数，客户端加入房间时也要使用相同的channelName字符串。cid是创建成功返回的房间唯一标识（long类型），不用于加入房间。

## 其他触发场景

（合并时在此处追加）
