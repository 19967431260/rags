---
track_type: 咨询类
sub_type: 功能实现咨询
product: IM-SDK
feature: 消息管理
platform: Server
title: 服务端实现消息自动撤回功能
root_cause: 
solution: 云信提供撤回接口，业务层需自行实现计时逻辑：1.发送消息时记录时间戳
2.通过消息抄送获取msgTimestamp
3.到达指定时间后调用撤回接口：https://doc.yunxin.163.com/messaging2/server-apis/jAwNTEzODQ
customers: ["上海盛世铭科技有限公司"]
source: chat_history
tags: ["自动撤回", "消息撤回", "服务端", "抄送"]
created: 2025-11-04
updated: 2026-03-20
---

## 问题：Server 服务端实现消息自动撤回功能

## 问题详情

**现象**：
客户咨询如何实现消息自动撤回功能。

**排查过程**：


## 问题原因



## 解决方案

云信提供撤回接口，业务层需自行实现计时逻辑：1.发送消息时记录时间戳
2.通过消息抄送获取msgTimestamp
3.到达指定时间后调用撤回接口：https://doc.yunxin.163.com/messaging2/server-apis/jAwNTEzODQ
