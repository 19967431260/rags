---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 消息推送
platform: HarmonyOS
title: 鸿蒙IM消息推送配置与接收问题
root_cause: 1. 服务密钥文件projectId配置错误；2. 营销类推送被华为频控限制
solution: 1. 使用正确的projectId(736430079245718997)创建服务密钥；2. 申请即时聊天类型的推送权限；3. 发送消息时设置harmonyField.payload.notification.category为聊天类型
customers: ["极氪"]
source: chat_history
tags: ["鸿蒙推送","华为推送","80300002","消息推送","频控"]
created: 2025-02-11
updated: 2025-03-20
---

## 问题：HarmonyOS 鸿蒙IM消息推送配置与接收问题

## 问题详情

**现象**：
鸿蒙端消息推送配置后，能够获取到pushToken，但杀掉app后收不到通知。华为推送返回错误码80300002：No permission to send message to these tmIDs。

## 排查过程

1. 确认pushToken获取正常 → 确认配置
2. 检查服务端推送日志，发现已推送到华为服务器 → 确认服务端正常
3. 华为返回错误码80300002，表示无权限发送消息 → 定位权限问题
4. 检查证书配置，发现projectId配置错误 → 定位配置错误
5. 重新配置正确的服务密钥文件后推送成功 → 修复配置
6. 但用户仅收到一次推送，后续收不到 → 发现新问题
7. 确认是营销类消息被华为频控 → 定位频控问题

**关键发现**：服务密钥文件projectId配置错误；营销类推送被华为频控限制

## 问题原因

1. 服务密钥文件projectId配置错误
2. 营销类推送被华为频控限制

## 解决方案

1. 使用正确的projectId(736430079245718997)创建服务密钥
2. 申请即时聊天类型的推送权限
3. 发送消息时设置harmonyField.payload.notification.category为聊天类型

## 其他触发场景

