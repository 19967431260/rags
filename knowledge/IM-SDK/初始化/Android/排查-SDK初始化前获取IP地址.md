---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 初始化
platform: Android
title: SDK初始化前获取IP地址
root_cause: SDK 9.19.4版本在初始化阶段会获取IP地址。
solution: 更新SDK至9.21.0或更高版本，该问题已在新版本中优化。参考最佳实践：https://doc.yunxin.163.com/messaging/guide/Tg3NDExMDA?platform=android
customers: ["深圳富旅奇缘", "深圳岚峰创视"]
source: chat_history
tags: ["9.21.0", "初始化", "隐私合规", "9.19.4", "IP获取"]
created: 2026-01-08
updated: 2026-03-15
---


## 问题：Android SDK初始化前获取IP地址

## 问题详情

**现象**：
Android SDK 9.19.4版本在授权前（初始化前）会获取IP地址，不符合隐私合规要求。

## 排查过程

1. 确认SDK版本 → 9.19.4
2. 检查调用栈 → 确认为SDK初始化相关
**关键发现**：旧版本SDK在初始化时会获取IP

## 问题原因

SDK 9.19.4版本在初始化阶段会获取IP地址。

## 解决方案

更新SDK至9.21.0或更高版本，该问题已在新版本中优化。参考最佳实践：https://doc.yunxin.163.com/messaging/guide/Tg3NDExMDA?platform=android
