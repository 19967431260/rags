---
track_type: 排查类
sub_type: 集成类
product: NERoom
feature: 房间管理
platform: Android
title: NoSuchMethodError EglBase.create()方法找不到
root_cause: 客户依赖配置中存在冲突，导致EglBase类加载错误。
solution: 检查并清理项目依赖，移除重复的RTC相关依赖包，确保依赖树正确。
customers: ["海南探寻未来科技有限责任公司"]
source: chat_history
tags: ["NoSuchMethodError", "EglBase", "joinRoom", "依赖冲突"]
created: 2025-11-28
updated: 2026-03-20
---

## 问题：Android NoSuchMethodError EglBase.create()方法找不到

## 问题详情

**现象**：
客户调用NERoom joinRoom时出现崩溃：java.lang.NoSuchMethodError: No static method create()Lcom/netease/lava/webrtc/EglBase。使用版本netease_roomkit: 1.30.14。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 确认错误信息 → EglBase.create()静态方法找不到
2. 检查依赖冲突 → 询问是否移除了额外的RTC引入包
3. 客户自查 → 发现是自身依赖问题
**关键发现**：客户依赖配置问题导致EglBase类冲突

**关键发现**：

## 问题原因

客户依赖配置中存在冲突，导致EglBase类加载错误。

## 解决方案

检查并清理项目依赖，移除重复的RTC相关依赖包，确保依赖树正确。

## 其他触发场景

