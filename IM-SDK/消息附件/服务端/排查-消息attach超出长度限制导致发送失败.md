---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息附件
platform: 服务端
title: 消息attach超出长度限制导致发送失败
root_cause: 消息attach字段超出4096字节长度限制
solution: 缩短attach字段内容，确保不超过4096字节限制
customers: ["杭州晓宇"]
source: chat_history
tags: ["IM-SDK", "attach", "414", "长度限制", "发送失败"]
created: 2025-05-14
updated: 2025-03-20
---

## 问题：服务端 消息attach超出长度限制导致发送失败

## 问题详情

**现象**：
消息发送返回code 414，attach exceed limit，limit 4096，attach超出长度限制。

## 排查过程

**关键发现**：消息attach字段超出4096字节长度限制

## 问题原因

消息attach字段超出4096字节长度限制

## 解决方案

缩短attach字段内容，确保不超过4096字节限制
