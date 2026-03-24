---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 集成
platform: Android
title: IM SDK basesdk依赖问题
root_cause: 可能是网络问题或AS问题。
solution: 检查maven仓库配置，重启AS试试。basesdk依赖会关联引入其他aar基础组件。
customers: ['河南明图计算机科技有限公司']
source: chat_history
tags: ['IM', 'basesdk', '依赖', 'Android', 'gradle']
created: 2025-02-25
updated: 2026-03-23
---

## 问题：Android IM SDK basesdk依赖问题

## 问题详情

**现象**：
集成IM SDK后basesdk文件找不到，gradle已引入但依赖没有加载成功。

**环境信息**：
- 平台：Android
- 产品：IM-SDK

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

（从会话提取排查过程）

## 问题原因

可能是网络问题或AS问题。

## 解决方案

检查maven仓库配置，重启AS试试。basesdk依赖会关联引入其他aar基础组件。

## 其他触发场景

（合并时在此处追加：`- [Android] IM SDK basesdk依赖问题，来源：['河南明图计算机科技有限公司']，2026-03-23`）
