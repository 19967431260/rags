---
track_type: 排查类
sub_type: 合规问题
product: IM-SDK
feature: 初始化
platform: Android
title: V9授权前SDK获取IP的合规问题
root_cause: V9.19.4版本SDK在初始化时会获取IP地址
solution: 更新到最新版本SDK（9.21.0），该问题已在今年优化过。参考最佳实践：https://doc.yunxin.163.com/messaging/guide/Tg3NDExMDA?platform=android
customers: ["深圳富旅奇缘"]
source: chat_history
tags: ["IP获取", "隐私合规", "初始化", "V9"]
created: 2026-01-08
updated: 2026-03-15
---

## 问题：Android V9授权前SDK获取IP的合规问题

## 问题详情

**现象**：
Android应用在用户同意隐私协议前，检测到云信SDK获取了IP地址，存在合规风险。

**环境信息**：
- SDK 版本：V9.19.4
- 平台：Android

## 排查过程

1. 检查授权前行为 → 发现SDK获取了IP
2. 确认初始化时机 → 业务侧在同意后才初始化
3. 查看调用栈 → 定位到SDK内部逻辑

**关键发现**：V9.19.4版本在初始化时会获取IP

## 问题原因

V9.19.4版本SDK在初始化时会获取IP地址

## 解决方案

更新到最新版本SDK（9.21.0），该问题已在今年优化过。参考最佳实践：https://doc.yunxin.163.com/messaging/guide/Tg3NDExMDA?platform=android

## 其他触发场景

- [Android] V9授权前SDK获取IP的合规问题，来源：['深圳富旅奇缘']，2026-03-15
