---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 登录
platform: Flutter
title: Flutter release包登录返回398错误
root_cause: 第三方回调登录时dynamicTokenProvider需要返回登录类型
solution: 配置防混淆规则，确保dynamicTokenProvider正确实现并返回登录类型，参考文档：https://doc.yunxin.163.com/messaging/guide/Dg5NjI4MDg?platform=flutter#编译与防混淆配置仅-android
customers: ["众腾人力"]
source: chat_history
tags: ["Flutter", "登录", "398", "release包", "混淆"]
created: 2025-06-13
updated: 2025-03-23
---

## 问题：Flutter Flutter release包登录返回398错误

## 问题详情

**现象**：
打release正式包后聊天登录code返回398，debug包正常，iOS正常。

**环境信息**：
- 平台：Flutter Android
- 问题仅在release包出现

## 排查过程

1. 检查防混淆配置 → 2. 确认第三方回调登录方式 → 3. 检查dynamicTokenProvider是否正确返回登录类型

## 问题原因

第三方回调登录时dynamicTokenProvider需要返回登录类型

## 解决方案

配置防混淆规则，确保dynamicTokenProvider正确实现并返回登录类型，参考文档：https://doc.yunxin.163.com/messaging/guide/Dg5NjI4MDg?platform=flutter#编译与防混淆配置仅-android
