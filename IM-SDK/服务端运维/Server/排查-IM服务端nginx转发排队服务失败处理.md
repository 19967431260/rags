---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 服务端运维
platform: Server
title: IM服务端nginx转发排队服务失败处理
root_cause: nginx转发不到排队服务
solution: 执行docker restart queue-server重启排队服务
customers: ["信雅达（晋商银行）"]
source: chat_history
tags: ["nginx", "queue-server", "转发失败", "示闲"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：Server IM服务端nginx转发排队服务失败处理

## 问题详情

**现象**：
测试环境出现nginx转发不到排队服务的报错，导致签入后示闲不了。

**环境信息**：
- 部署环境：测试环境

## 排查过程

1. 检查磁盘是否已满 → 确认磁盘状态
2. 重启queue-server服务 → 解决转发问题

**关键发现**：nginx转发不到排队服务

## 问题原因

nginx转发不到排队服务

## 解决方案

执行docker restart queue-server重启排队服务

## 其他触发场景

（无）
