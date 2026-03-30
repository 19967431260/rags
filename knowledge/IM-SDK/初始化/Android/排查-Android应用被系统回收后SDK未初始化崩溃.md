---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 初始化
platform: Android
title: Android应用被系统回收后SDK未初始化崩溃
root_cause: 
solution: SDK方法调用前必须先初始化和登录，业务侧调用前需做防御判断；确保在Application#onCreate中初始化SDK，系统回收后恢复会重新走初始化流程
customers: ["VIP-云信-河北家和康孕"]
source: chat_history
tags: ["Android", "SDK初始化", "崩溃", "系统回收", "Application", "onCreate"]
created: 2025-11-17
updated: 2026-03-20
---

## 问题：Android Android应用被系统回收后SDK未初始化崩溃

## 问题详情

**现象**：
Android应用长时间放后台被系统回收后，再次打开恢复页面时，调用聊天API出现SDK未初始化的崩溃信息；小米澎湃系统尤其严重，其他系统可能崩溃后重启

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 确认是否在Application中初始化SDK → 客户确认已初始化
2. 分析系统回收后恢复流程 → 正常情况下应走到Application#onCreate，不会跳过SDK init流程
3. 建议客户测试验证是否走到初始化流程

**关键发现**：

## 问题原因



## 解决方案

SDK方法调用前必须先初始化和登录，业务侧调用前需做防御判断；确保在Application#onCreate中初始化SDK，系统回收后恢复会重新走初始化流程

## 其他触发场景

