---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 历史消息
platform: 安卓
title: getMessagesDynamically查询消息数量不足
root_cause: 客户端对重复uuid消息进行去重，导致返回数量少于limit；重复消息由用户多次点击重发产生
solution: 业务层优化重发逻辑，发送成功后隐藏重发按钮或改为转圈状态，防止重复发送
customers: ["VIP云信-东莞市伊洛信息科技有限公司"]
source: chat_history
tags: ["getMessagesDynamically", "消息去重", "uuid", "重发", "消息数量"]
created: 2025-02-20
updated: 2026-03-20
---

## 问题：安卓 getMessagesDynamically查询消息数量不足

## 问题详情

**现象**：
调用getMessagesDynamically查询消息，设置limit为50但返回49条

## 排查过程

1. 分析日志 → 服务端返回50条
2. 对比客户端结果 → 客户端去重后49条
3. 确认原因 → 存在两条完全相同的uuid消息

## 问题原因

客户端对重复uuid消息进行去重，导致返回数量少于limit；重复消息由用户多次点击重发产生

## 解决方案

业务层优化重发逻辑，发送成功后隐藏重发按钮或改为转圈状态，防止重复发送

## 其他触发场景

