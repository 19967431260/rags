---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 离线推送
platform: Android
title: 华为推送报错certificate fingerprint error
root_cause: 华为推送需要配置应用的SHA256指纹证书
solution: 在华为开发者平台配置应用的SHA256指纹证书。
customers: ["VIP云信-郑州开缘商贸有限公司"]
source: chat_history
tags: ["华为推送", "6003", "certificate fingerprint", "SHA256"]
created: 2025-11-10
updated: 2026-03-20
---

## 问题：Android 华为推送报错certificate fingerprint error

## 问题详情

**现象**：
华为推送集成后报错，日志显示query token with exception 6003: certificate fingerprint error，无法获取token。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 检查日志 → 发现6003错误码
2. 查询华为文档 → certificate fingerprint error
**关键发现**：华为推送需要配置SHA256指纹

**关键发现**：

## 问题原因

华为推送需要配置应用的SHA256指纹证书

## 解决方案

在华为开发者平台配置应用的SHA256指纹证书。

## 其他触发场景

