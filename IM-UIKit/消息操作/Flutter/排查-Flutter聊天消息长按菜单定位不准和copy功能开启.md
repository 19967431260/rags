---
track_type: 排查类
sub_type: 使用问题
product: IM-UIKit
feature: 消息操作
platform: Flutter
title: Flutter聊天消息长按菜单定位不准和copy功能开启
root_cause: copy功能默认未开启；菜单位置问题可能是viewportBottom计算未考虑标题栏高度。
solution: copy功能：在ChatUIConfig中配置开启消息复制功能（chatUIConfig的popMenuCopyConfig）；菜单位置问题需等待SDK修复或自行计算viewportBottom时考虑标题栏高度。
customers: ["仁人数字化科技（山东）有限公司"]
source: chat_history
tags: ["Flutter", "长按菜单", "copy", "viewportBottom", "定位"]
created: 2025-08-08
updated: 2026-03-26
---

## 问题：Flutter Flutter聊天消息长按菜单定位不准和copy功能开启

## 问题详情

**现象**：
Flutter聊天消息长按菜单定位不准，且copy功能无法使用。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：Flutter
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

**关键发现**：copy功能默认未开启；菜单位置问题可能是viewportBottom计算未考虑标题栏高度

## 问题原因

copy功能默认未开启；菜单位置问题可能是viewportBottom计算未考虑标题栏高度。

## 解决方案

copy功能：在ChatUIConfig中配置开启消息复制功能（chatUIConfig的popMenuCopyConfig）；菜单位置问题需等待SDK修复或自行计算viewportBottom时考虑标题栏高度。

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
