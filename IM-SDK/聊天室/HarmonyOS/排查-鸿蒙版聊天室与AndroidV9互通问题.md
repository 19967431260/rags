---
track_type: 排查类
sub_type: 测试问题
product: IM-SDK
feature: 聊天室
platform: HarmonyOS
title: 鸿蒙版聊天室与Android V9互通问题
root_cause: V9与V10协议存在差异，10.6.0版本较老
solution: 建议升级鸿蒙SDK到10.8.10版本，使用github.com/netease-kit/nim-uikit-harmony中的最新版本
customers: ["上海麦色"]
source: chat_history
tags: ["鸿蒙", "聊天室", "V9", "V10", "互通", "10.6.0"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：鸿蒙版聊天室与Android V9互通问题

## 问题详情

**现象**：
鸿蒙V10聊天室与Android V9版本存在消息互通问题：1)禁言/解禁状态消息类型无法区分 2)公告信息获取为undefined 3)remoteExtension扩展信息接收不到。

**环境信息**：
- 平台：HarmonyOS

## 排查过程

1. 确认Android端版本为V9而非V10
2. 分析消息体结构差异
3. 建议升级鸿蒙SDK版本到10.8.10

## 根因分析

V9与V10协议存在差异，10.6.0版本较老

## 解决方案

建议升级鸿蒙SDK到10.8.10版本，使用github.com/netease-kit/nim-uikit-harmony中的最新版本

## 其他触发场景

（无）
