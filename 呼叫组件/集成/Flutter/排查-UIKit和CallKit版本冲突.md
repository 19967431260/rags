---
track_type: 排查类
sub_type: 集成类
product: 呼叫组件
feature: 集成
platform: Flutter
title: UIKit和CallKit版本冲突
root_cause: nim_chatkit_ui里面引入了callkit，版本依赖冲突。
solution: 1. 更新UIKit到最新版本；2. 在dependency_overrides中强制覆盖netease_callkit_ui版本；3. 执行flutter clean和flutter pub get。
customers: ["VIP云信-山东华志汇-StarLink"]
source: chat_history
tags: ["UIKit", "CallKit", "版本冲突", "dependency_overrides", "Flutter"]
created: 2025-11-10
updated: 2026-03-20
---

## 问题：Flutter UIKit和CallKit版本冲突

## 问题详情

**现象**：
集成UIKit时包含nim_core_v2，与dependency_overrides强制升级的nim_core_v2有冲突，最新版UIKit和CallKit不匹配。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 检查依赖冲突信息；2. 确认nim_chatkit_ui和netease_callkit_ui版本兼容性。

**关键发现**：

## 问题原因

nim_chatkit_ui里面引入了callkit，版本依赖冲突。

## 解决方案

1. 更新UIKit到最新版本；2. 在dependency_overrides中强制覆盖netease_callkit_ui版本；3. 执行flutter clean和flutter pub get。

## 其他触发场景

