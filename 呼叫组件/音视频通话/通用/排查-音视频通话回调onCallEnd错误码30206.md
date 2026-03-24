---
track_type: 排查类
sub_type: 使用问题
product: 呼叫组件
feature: 音视频通话
platform: 通用
title: 音视频通话回调onCallEnd错误码30206
root_cause: 服务端调用了踢人接口/v3/api/kicklist/members导致用户被踢出房间
solution: 检查业务层调用踢人接口的逻辑，确认是否需要踢人操作
customers: ['新余元声网络技术']
source: chat_history
tags: ['30206', 'onCallEnd', '踢人', '呼叫组件']
created: 2025-02-24
updated: 2026-03-23
---

## 问题：通用 音视频通话回调onCallEnd错误码30206

## 问题详情

**现象**：
音视频通话时触发onCallEnd回调，reasonCode=10，message='local rtc disconnected with reason code 30206'

**环境信息**：
- 平台：通用
- 产品：呼叫组件

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 提供uid和房间cid → 技术支持查询通话记录
2. 发现服务端有调用踢人接口的记录
3. 确认是服务端调用踢人接口导致本地SDK提示和服务器断开

## 问题原因

服务端调用了踢人接口/v3/api/kicklist/members导致用户被踢出房间

## 解决方案

检查业务层调用踢人接口的逻辑，确认是否需要踢人操作

## 其他触发场景

（合并时在此处追加：`- [通用] 音视频通话回调onCallEnd错误码30206，来源：['新余元声网络技术']，2026-03-23`）
