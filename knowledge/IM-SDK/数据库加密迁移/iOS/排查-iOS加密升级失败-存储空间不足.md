---
track_type: 排查类
sub_type: 迁移失败
product: IM-SDK
feature: 数据库加密迁移
platform: iOS
title: iOS加密升级失败-存储空间不足
root_cause: 设备可用存储空间不足（需要约2.8G，实际可用约2.4G），迁移被主动暂停而非失败
solution: 释放存储空间后下次启动会继续迁移；可通过disableFreeSpaceCheck选项关闭空间检查
customers: ["ISV云信私有化-顺丰科技-多项目"]
source: chat_history
tags: ["加密迁移", "iOS", "存储空间", "迁移暂停"]
created: 2025-12-09
updated: 2026-03-23
---

## 问题：iOS加密升级失败-存储空间不足

## 问题详情

**现象**：
iOS用户加密升级失败，日志显示迁移状态异常。用户存储显示还有7G，但系统返回可用空间不足。

**环境信息**：
- 产品：IM-SDK
- 功能：数据库加密迁移
- 平台：iOS

## 排查过程

1. 分析日志发现NSFileSystemFreeSize = 2383482880 (约2.4G)
2. 计算所需空间required size 2838727501 (约2.8G)
3. 确认是存储空间不足导致迁移暂停
4. 发现回调信息没有明确提示空间不足

**关键发现**：设备可用存储空间不足，迁移被主动暂停而非失败

## 问题原因

设备可用存储空间不足（需要约2.8G，实际可用约2.4G），迁移被主动暂停而非失败。

## 解决方案

1. 释放存储空间后下次启动会继续迁移
2. 可通过disableFreeSpaceCheck选项关闭空间检查

## 其他触发场景

