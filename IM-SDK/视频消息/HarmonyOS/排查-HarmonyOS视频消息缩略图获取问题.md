---
track_type: "排查类"
sub_type: "使用问题"
product: "IM-SDK"
feature: "视频消息"
platform: "HarmonyOS"
title: "HarmonyOS视频消息缩略图获取问题"
root_cause: "缩略图尺寸150*0导致生成异常"
solution: "检查获取缩略图时的长宽参数设置，参考官方缩略图生成规则"
customers: ["北京耘想科技"]
source: "chat_history"
tags: ["HarmonyOS", "视频消息", "缩略图", "150x0"]
created: "2025-09-01"
updated: "2026-03-20"
---

## 问题：HarmonyOS HarmonyOS视频消息缩略图获取问题

## 问题详情

**现象**：
客户询问HarmonyOS视频消息的消息体里是否有缩略图，以及获取的缩略图无法加载。

## 排查过程

1. 询问是否有缩略图 → 使用storageService的getImageThumbUrl
2. 客户反馈无法加载 → 询问是url获取不到还是无法加载
3. 客户提供截图 → 发现获取的长宽是150*0
4. 分析原因 → 缩略图生成规则可能有问题
5. 建议测试 → 研发测试缩略图生成

## 问题原因

缩略图尺寸150*0导致生成异常

## 解决方案

检查获取缩略图时的长宽参数设置，参考官方缩略图生成规则

## 其他触发场景
