---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 消息查询
platform: Flutter
title: Flutter Windows端打包后会话列表为空
root_cause: Flutter Windows需要使用NimPCSDK，不能使用nim_core_v2通用SDK。
solution: Windows和Mac平台需要切换到NimPCSDK。Flutter uikit for Windows目前有已知限制，客服反馈flutter v10 uikit还没有支持windows，可能存在未知兼容性问题。
customers: ["voiceverse.org"]
source: chat_history
tags: ["Flutter", "Windows", "NimPCSDK", "会话列表", "release"]
created: 2025-08-28
updated: 2025-08-28
---

## 问题：Flutter Flutter Windows端打包后会话列表为空

## 问题详情

**现象**：
Flutter编译到Windows平台，debug模式会话列表正常显示，但release模式打包成exe后会话列表为空。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：Flutter Windows
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客服拉取SDK日志 → 获取排查信息
2. 日志分析显示enableCloudConversation=false → 发现配置问题
3. 多次排查确认配置已改但仍无效 → 深入排查
4. 最终确认Windows和Mac需要使用NimPCSDK → 定位根因

**关键发现**：Flutter Windows不支持使用通用SDK，必须使用专门的PC SDK

## 问题原因

Flutter Windows需要使用NimPCSDK，不能使用nim_core_v2通用SDK。

## 解决方案

Windows和Mac平台需要切换到NimPCSDK。Flutter uikit for Windows目前有已知限制，客服反馈flutter v10 uikit还没有支持windows，可能存在未知兼容性问题。

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
