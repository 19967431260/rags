---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: iOS适配
platform: iOS
title: Xcode16打包提示包含bitcode
root_cause: Xcode16检测问题
solution: 执行命令xcrun bitcode_strip -r XXX -o XXX去除bitcode，或等Xcode更新
customers: ["湖南金生水科技"]
source: chat_history
tags: ["IM-SDK", "iOS", "Xcode16", "bitcode", "打包"]
created: 2025-05-06
updated: 2025-03-20
---

## 问题：iOS Xcode16打包提示包含bitcode

## 问题详情

**现象**：
使用Xcode16打包提示包含bitcode，但SDK已去除bitcode，可能是Xcode检测问题。

## 排查过程

**关键发现**：Xcode16检测问题

## 问题原因

Xcode16检测问题

## 解决方案

执行命令xcrun bitcode_strip -r XXX -o XXX去除bitcode，或等Xcode更新
