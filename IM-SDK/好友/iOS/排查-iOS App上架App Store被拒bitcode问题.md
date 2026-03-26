---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 好友
platform: iOS
title: iOS App上架App Store被拒bitcode问题
root_cause: 云信 SDK 某些版本中包含 bitcode，而 Apple 已不再支持 bitcode
solution: 参考云信官方文档 iOS 相关问题排查：https://doc.yunxin.163.com/messaging2/faq/jE4MjAwMTI?platform=client
customers: ["安徽鼎红科技有限公司"]
source: chat_history
tags: ["App Store","bitcode","上架被拒","ITMS-90482","NERtcSDK"]
created: 2025-08-17
updated: 2026-03-26
---

## 问题：iOS iOS App上架App Store被拒bitcode问题

## 问题详情

**现象**：
客户 App 上架 App Store Connect 时被拒，多个 NERtcSDK 相关 Framework 包含 bitcode。错误包括：ITMS-90482: Invalid Executable，包含 bitcode 的 framework 有 NERtcPersonSegment、NERtcSDK、NERtcnn、NIMNOS、YXAlog_iOS。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客服让客户参考云信文档解决 → 文档参考

**关键发现**：云信 SDK 某些版本中包含 bitcode，而 Apple 已不再支持 bitcode

## 问题原因

云信 SDK 某些版本中包含 bitcode，而 Apple 已不再支持 bitcode

## 解决方案

参考云信官方文档 iOS 相关问题排查：https://doc.yunxin.163.com/messaging2/faq/jE4MjAwMTI?platform=client

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
