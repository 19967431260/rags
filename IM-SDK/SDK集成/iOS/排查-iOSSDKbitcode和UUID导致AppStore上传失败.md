---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: SDK集成
platform: iOS
title: iOS SDK bitcode和UUID导致AppStore上传失败
root_cause: SDK版本较老，缺少符号表dysm文件
solution: bitcode按文档处理，UUID警告理论上不影响上传，如需要可提供dysm文件
customers: ["深圳招银国际"]
source: chat_history
tags: ["bitcode", "UUID", "AppStore", "iOS", "上传失败"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：iOS iOS SDK bitcode和UUID导致AppStore上传失败

## 问题详情

**现象**：
iOS打包上传AppStore遇到SDK包含bitcode和UUID的问题。

**环境信息**：
- 平台：iOS

## 排查过程

1. 处理bitcode问题 → 按文档方案执行
2. 处理UUID警告 → 确认是缺少符号表
3. 验证上传 → 警告不影响实际上传成功

**关键发现**：SDK版本较老，缺少符号表dysm文件

## 问题原因

SDK版本较老，缺少符号表dysm文件

## 解决方案

bitcode按文档处理，UUID警告理论上不影响上传，如需要可提供dysm文件

## 其他触发场景

（无）
