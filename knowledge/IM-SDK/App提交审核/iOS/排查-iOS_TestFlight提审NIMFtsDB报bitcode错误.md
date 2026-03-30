---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: App提交审核
platform: iOS
title: iOS TestFlight提审NIMFtsDB报bitcode错误
root_cause: 第三方库NIMFtsDB包含bitcode，但Xcode处理时出错
solution: 使用bitcode移除工具处理NIMFtsDB库：xcrun bitcode_strip -r NIMFtsDB.framework/NIMFtsDB -o NIMFtsDB.framework/NIMFtsDB
customers: ["仁人数字化科技（山东）有限公司"]
source: chat_history
tags: ["iOS", "TestFlight", "bitcode", "NIMFtsDB", "Xcode"]
created: 2025-08-08
updated: 2026-03-26
---

## 问题：iOS iOS TestFlight提审NIMFtsDB报bitcode错误

## 问题详情

**现象**：
iOS TestFlight提审时报NIMFtsDB bitcode错误。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：iOS
- 其他：TestFlight提审

**相关日志**：
NIMFtsDB bitcode错误

## 排查过程

**关键发现**：第三方库NIMFtsDB包含bitcode，但Xcode处理时出错

## 问题原因

第三方库NIMFtsDB包含bitcode，但Xcode处理时出错

## 解决方案

使用bitcode移除工具处理NIMFtsDB库：xcrun bitcode_strip -r NIMFtsDB.framework/NIMFtsDB -o NIMFtsDB.framework/NIMFtsDB

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
