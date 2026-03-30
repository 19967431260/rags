---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 初始化
platform: Android
title: SDK 9.19.4版本初始化前获取IP地址不符合隐私合规
root_cause: SDK 9.19.4版本在初始化阶段会获取IP地址。
solution: 更新到最新版本即可解决该隐私合规问题。
customers: ["智慧丘比特"]
source: chat_history
tags: ["IP获取", "隐私合规", "9.19.4", "初始化"]
created: 2026-01-16
updated: 2026-03-15
---

## 问题：Android SDK 9.19.4版本初始化前获取IP地址不符合隐私合规

## 问题详情

**现象**：
安卓市场检测出在用户同意隐私协议前获取IP，调用堆栈显示为云信SDK调用。SDK版本9.19.4。

## 排查过程

1. 确认SDK版本 → 9.19.4
2. 检查调用堆栈 → 确认为SDK初始化相关

## 问题原因

SDK 9.19.4版本在初始化阶段会获取IP地址。

## 解决方案

更新到最新版本即可解决该隐私合规问题。
