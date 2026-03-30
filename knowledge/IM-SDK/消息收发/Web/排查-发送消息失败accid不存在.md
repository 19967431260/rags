---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息收发
platform: Web
title: 发送消息失败accid不存在
root_cause: 客户使用了业务侧的用户ID而非云信的accid
solution: 确认接收方的正确accid，使用云信返回的accid而不是业务侧的用户ID作为to参数
customers: ["111医药馆"]
source: chat_history
tags: ["消息发送失败", "accid", "P2P消息", "用户不存在"]
created: 2026-02-08
updated: 2026-03-17
---

## 问题：Web 发送消息失败accid不存在

## 问题详情

**现象**：
Web端发送P2P消息时status为fail，to参数为10011802，对方能给我发送消息但我无法发送给对方。

## 排查过程

1. 检查to参数10011802 → 查询该accid不存在
2. 核实对方实际accid → 确认对方accid应该是dangna而不是10011802

**关键发现**：客户使用了错误的accid

## 问题原因

客户使用了业务侧的用户ID而非云信的accid

## 解决方案

确认接收方的正确accid，使用云信返回的accid而不是业务侧的用户ID作为to参数

## 其他触发场景

（暂无）
