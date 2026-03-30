---
track_type: 排查类
sub_type: 使用问题
product: NERoom
feature: 成员管理
platform: Server
title: NERoom禁言后用户仍可发言
root_cause: 房间模板中audience角色开启了'全局禁言'权限，导致禁言对该角色不生效
solution: 在管理后台关闭audience角色的'全局禁言'权限，修改模板后重新创建房间生效
customers: ['河南新秀金文化传媒']
source: chat_history
tags: ['禁言', '权限', '模板配置', '角色', 'audience']
created: 2025-01-20
updated: 2026-03-23
---

## 问题：Server NERoom禁言后用户仍可发言

## 问题详情

**现象**：
调用禁言接口成功后，被禁言用户仍可在房间内发送消息。

## 排查过程

1. 确认禁言接口调用成功
2. 检查房间模板配置
3. 确认角色权限设置

## 问题原因

房间模板中audience角色开启了'全局禁言'权限，导致禁言对该角色不生效

## 解决方案

在管理后台关闭audience角色的'全局禁言'权限，修改模板后重新创建房间生效

## 其他触发场景

（合并时在此处追加）
