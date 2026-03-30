---
track_type: 排查类
sub_type: 配置开通咨询
product: IM-UIKit
feature: 会话管理
platform: Android
title: 创建云信会话返回403 forbidden错误
root_cause: 云端会话功能未开启
solution: 登录云信控制台，进入应用管理界面，开启云端会话功能
customers: ['巽风科技']
source: chat_history
tags: ['403', 'forbidden', '创建会话', '云端会话', 'UIKit']
created: 2025-02-11
updated: 2026-03-23
---

## 问题：Android 创建云信会话返回403 forbidden错误

## 问题详情

**现象**：
Android端使用IM UIKit创建云信会话时返回403错误，code=403, desc=forbidden。客户使用SDK版本10.6.0。

**环境信息**：
- 平台：Android
- 产品：IM-UIKit

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

（从会话提取排查过程）

## 问题原因

云端会话功能未开启

## 解决方案

登录云信控制台，进入应用管理界面，开启云端会话功能

## 其他触发场景

（合并时在此处追加：`- [Android] 创建云信会话返回403 forbidden错误，来源：['巽风科技']，2026-03-23`）
