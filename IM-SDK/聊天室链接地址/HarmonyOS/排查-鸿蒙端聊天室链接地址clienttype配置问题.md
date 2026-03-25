---
track_type: "排查类"
sub_type: "集成类"
product: "IM-SDK"
feature: "聊天室链接地址"
platform: "HarmonyOS"
title: "鸿蒙端聊天室链接地址clienttype配置问题"
root_cause: "鸿蒙是偏Web技术栈，服务端获取地址时clienttype需要给1，但配置了2（Android/iOS用）"
solution: "鸿蒙端获取聊天室链接地址时，clienttype应配置为1（Web端），而不是2"
customers: ["智己"]
source: "chat_history"
tags: ["鸿蒙", "聊天室", "链接地址", "clienttype"]
created: "2025-09-28"
updated: "2026-03-20"
---

## 问题：HarmonyOS 鸿蒙端聊天室链接地址clienttype配置问题

## 问题详情

**现象**：
鸿蒙端直接使用地址链接失败，但使用getChatroomLinkAddress获取的地址可以链接成功

## 排查过程

1. 分析地址差异 → 手动配置的地址与服务端获取的地址不同
2. 确认clienttype → 鸿蒙偏Web技术栈，clienttype应给1
3. 验证解决方案 → 修改clienttype后地址正确
**关键发现**：鸿蒙端clienttype应配置为1（Web端）而非2（Android/iOS）

## 问题原因

鸿蒙是偏Web技术栈，服务端获取地址时clienttype需要给1，但配置了2（Android/iOS用）

## 解决方案

鸿蒙端获取聊天室链接地址时，clienttype应配置为1（Web端），而不是2

## 其他触发场景
