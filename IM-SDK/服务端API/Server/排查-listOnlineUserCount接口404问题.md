---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 服务端API
platform: Server
title: listOnlineUserCount接口404问题
root_cause: 私有化服务器不支持listOnlineUserCount接口。
solution: 私有化环境不支持该接口，需要使用其他方式实现功能。
customers: ['千橡']
source: chat_history
tags: ['404', 'listOnlineUserCount', '私有化', '服务端API']
created: 2025-01-03
updated: 2026-03-23
---

## 问题：Server listOnlineUserCount接口404问题

## 问题详情

**现象**：
客户调用/team/listOnlineUserCount.action接口返回404。

## 排查过程

1. 客户反馈接口404 → 技术支持确认服务器是否支持该接口
2. 确认私有化服务器没有这个接口

## 问题原因

私有化服务器不支持listOnlineUserCount接口。

## 解决方案

私有化环境不支持该接口，需要使用其他方式实现功能。

## 其他触发场景

（合并时在此处追加）
