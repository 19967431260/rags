---
track_type: "排查类"
sub_type: "集成类"
product: "IM-SDK"
feature: "Flutter集成"
platform: "Flutter"
title: "Flutter SDK升级后Kotlin编译报错"
root_cause: "Flutter SDK升级后缓存未清理，导致旧版本缓存与新版本代码冲突"
solution: "执行Flutter clean清理缓存，然后执行Flutter pub get重新获取依赖。"
customers: ["LINKCOM NETWORK"]
source: "chat_history"
tags: ["IM", "Flutter", "升级", "Kotlin", "编译错误"]
created: "2025-09-10"
updated: "2026-03-20"
---

## 问题：Flutter Flutter SDK升级后Kotlin编译报错

## 问题详情

**现象**：
云信nim_core flutter版本从1.8.3升级到1.9.0+1后，编译报错Unresolved reference: AttachmentHelper/FLTInitializeService等。

## 排查过程

1. 确认升级版本 → 从1.8.3升级到1.9.0+1
2. 分析报错信息 → Kotlin代码找不到引用
3. 执行清理重建 → Flutter clean + Flutter pub get

## 问题原因

Flutter SDK升级后缓存未清理，导致旧版本缓存与新版本代码冲突

## 解决方案

执行Flutter clean清理缓存，然后执行Flutter pub get重新获取依赖。

## 其他触发场景
