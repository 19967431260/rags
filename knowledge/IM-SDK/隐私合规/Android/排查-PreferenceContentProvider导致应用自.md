---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 隐私合规
platform: Android
title: "PreferenceContentProvider导致应用自启动"
root_cause: "SDK 9.2.5版本的PreferenceContentProvider会导致应用自启动，影响隐私合规审核。"
solution: "1. 升级SDK到9.5.0或更高版本；2. 初始化时配置disableawake禁用自启动；3. SDK 9.5.0已内部兼容PreferenceContentProvider配置，无需手动添加到AndroidManifest。"
customers: ["中原地产", "VIP云信-中原地产"]
source: chat_history
tags: ["PreferenceContentProvider", "自启动", "隐私合规", "disableawake"]
created: 2026-01-04
updated: 2026-03-15
---

## 问题：Android PreferenceContentProvider导致应用自启动

## 问题详情

**现象**：
应用在巨量引擎审核时被检测到自启动行为，关联到PreferenceContentProvider组件。应用杀掉后会自动重启。

## 排查过程

1. 检查AndroidManifest配置 → PreferenceContentProvider已声明
2. 查询自启动原因 → 确认与SDK的PreferenceContentProvider有关
**关键发现**：SDK 9.2.5版本存在自启动问题，需要升级并配置disableawake。

## 问题原因

SDK 9.2.5版本的PreferenceContentProvider会导致应用自启动，影响隐私合规审核。

## 解决方案

1. 升级SDK到9.5.0或更高版本；2. 初始化时配置disableawake禁用自启动；3. SDK 9.5.0已内部兼容PreferenceContentProvider配置，无需手动添加到AndroidManifest。

## 其他触发场景
- [Android] PreferenceContentProvider导致应用自启动，来源：中原地产，2026-03-15


（暂无）
