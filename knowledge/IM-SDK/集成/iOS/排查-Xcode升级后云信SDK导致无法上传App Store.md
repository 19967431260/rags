---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 集成
platform: iOS
title: Xcode升级后云信SDK导致无法上传App Store
root_cause: Xcode升级后对bitcode的处理方式变化，云信SDK部分库包含bitcode导致上传失败
solution: 手动移除云信SDK相关库的bitcode，参考文档: https://doc.yunxin.163.com/messaging2/faq/jE4MjAwMTI?platform=client
customers: ['VIP云信-中原地产']
source: chat_history
tags: ['Xcode', 'bitcode', 'iOS', '上传', 'AppStore']
created: 2025-02-10
updated: 2026-03-23
---

## 问题：iOS Xcode升级后云信SDK导致无法上传App Store

## 问题详情

**现象**：
客户升级Xcode后上传App新版本时因云信SDK报错导致无法上传更新版本

**环境信息**：
- 平台：iOS
- 产品：IM-SDK

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客户使用Xcode 16.2版本
2. 检查报错信息与bitcode相关
**关键发现**：Xcode新版本对bitcode要求变化，需要手动移除相关库

## 问题原因

Xcode升级后对bitcode的处理方式变化，云信SDK部分库包含bitcode导致上传失败

## 解决方案

手动移除云信SDK相关库的bitcode，参考文档: https://doc.yunxin.163.com/messaging2/faq/jE4MjAwMTI?platform=client

## 其他触发场景

（合并时在此处追加：`- [iOS] Xcode升级后云信SDK导致无法上传App Store，来源：['VIP云信-中原地产']，2026-03-23`）
