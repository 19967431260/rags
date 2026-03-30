---
track_type: 排查类
sub_type: 集成类
product: RTC
feature: 屏幕共享
platform: iOS
title: iOS屏幕共享Extension Bundle ID重复
root_cause: 主 target 和 screen extension 使用了重复的 framework 引入；同时 screen extension 的 bundle ID 与主 app 不匹配
solution: 1. 将 pod 'NERtcCallKit/ScreenShare' 替换为 pod 'NERtcSDK_Special/ScreenShare', '5.6.2008'\n2. screen extension 的 bundle ID 应为 com.xxx.xxx.screen（带 .screen 后缀），但需要与主 app 有相同前缀\n3. group ID 应设为 group + 主 bundle ID（不要加 .screen 后缀）\n4. debug run 时 extension 也需被勾选同时运行
customers: ["袋鼠管家"]
source: chat_history
tags: ["NERtcReplayKit","屏幕共享","bundle ID","构建循环","iOS"]
created: 2025-08-11
updated: 2026-03-26
---

## 问题：iOS iOS屏幕共享Extension Bundle ID重复

## 问题详情

**现象**：
客户在 Flutter 集成 iOS 屏幕共享时报错 'Multiple commands produce NERtcReplayKit.framework'，打包构建时出现循环依赖。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客服建议将 pod 'NERtcCallKit/ScreenShare' 替换为 pod 'NERtcSDK_Special/ScreenShare' → 版本替换
2. 替换后仍出现构建循环 → 进一步排查
3. 最终排查发现 bundle ID 配置有误 → 配置问题

**关键发现**：主 target 和 screen extension 使用了重复的 framework 引入；同时 screen extension 的 bundle ID 与主 app 不匹配

## 问题原因

主 target 和 screen extension 使用了重复的 framework 引入；同时 screen extension 的 bundle ID 与主 app 不匹配

## 解决方案

1. 将 pod 'NERtcCallKit/ScreenShare' 替换为 pod 'NERtcSDK_Special/ScreenShare', '5.6.2008'
2. screen extension 的 bundle ID 应为 com.xxx.xxx.screen（带 .screen 后缀），但需要与主 app 有相同前缀
3. group ID 应设为 group + 主 bundle ID（不要加 .screen 后缀）
4. debug run 时 extension 也需被勾选同时运行

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
