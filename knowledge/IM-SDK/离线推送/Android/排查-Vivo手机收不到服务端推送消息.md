---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 离线推送
platform: Android
title: Vivo手机收不到服务端推送消息
root_cause: 客户端推送配置有问题，导致Vivo推送token未生成
solution: 检查客户端推送文档配置，确保Vivo推送初始化和token注册流程正确。
customers: ["四川捷登科技有限公司"]
source: chat_history
tags: ["Vivo推送", "推送token", "业务消息", "客户端配置"]
created: 2026-01-06
updated: 2026-03-15
---

## 问题：Android Vivo手机收不到服务端推送消息

## 问题详情

**现象**：
服务器调用推送API发送业务消息，Vivo手机无法接收到推送，但聊天消息可以正常收到推送。

## 排查过程

1. 尝试获取SDK日志 → Uniapp无法获取标准路径日志
2. 远程拉取推送token → 发现没有推送token生成
**关键发现**：客户端未生成Vivo推送token

## 问题原因

客户端推送配置有问题，导致Vivo推送token未生成

## 解决方案

检查客户端推送文档配置，确保Vivo推送初始化和token注册流程正确。
