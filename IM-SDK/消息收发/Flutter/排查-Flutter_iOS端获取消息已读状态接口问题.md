---
track_type: 排查类
sub_type: SDK缺陷
product: IM-SDK
feature: 消息收发
platform: Flutter
title: Flutter iOS端获取消息已读状态接口问题
root_cause: Flutter SDK iOS端10.4.0-10.5.0版本的已知问题
solution: 建议升级到最新版本，或联系技术支持获取修复方案
customers: ["重庆沁兴文化传媒有限公司"]
source: chat_history
tags: ["IM V10","Flutter","iOS","已读状态"]
created: 2025-05-09
updated: 2025-03-23
---

## 问题：Flutter Flutter iOS端获取消息已读状态接口问题

## 问题详情

**现象**：
客户使用Flutter SDK iOS端，调用isPeerRead接口获取消息已读状态时，在会话中发消息返回true，返回会话列表再次进入会话后全部显示false。

**环境信息**：
- 平台：Flutter iOS
- SDK版本：10.4.0-10.5.0
- 功能：消息已读状态

## 排查过程

1. 确认问题现象 → isPeerRead接口返回状态不一致
2. 分析SDK版本 → 10.4.0-10.5.0版本
3. 确认问题原因 → 已知问题
4. 提供解决方案 → 升级版本或联系技术支持

**关键发现**：这是Flutter SDK iOS端10.4.0-10.5.0版本的已知问题

## 问题原因

这是Flutter SDK iOS端10.4.0-10.5.0版本的已知问题。

## 解决方案

建议升级到最新版本，或联系技术支持获取修复方案。

## 其他触发场景

