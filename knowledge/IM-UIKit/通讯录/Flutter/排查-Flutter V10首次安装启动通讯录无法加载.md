---
track_type: 排查类
sub_type: 集成类
product: IM-UIKit
feature: 通讯录
platform: Flutter
title: Flutter V10首次安装启动通讯录无法加载
root_cause: ContactProvider注册时机问题，页面在IMKitClient.init完成前就加载了通讯录页面，导致依赖注入失败
solution: 将IMKitClient.init提前到登录页面打开时执行，确保在加载ContactPage之前完成UIKit初始化
customers: ["东莞市仁众丽科技有限公司"]
source: chat_history
tags: ["Flutter", "V10", "UIKit", "通讯录", "GetIt", "ContactProvider", "初始化"]
created: 2025-05-15
updated: 2025-03-20
---

## 问题：Flutter Flutter V10首次安装启动通讯录无法加载

## 问题详情

**现象**：
部分机型首次安装打开应用时，通讯录UI无法显示，报错GetIt: Object/factory with type ContactProvider is not registered。重新打开APP后正常，仅在首次安装时出现。

**环境信息**：
- SDK 版本：
- 系统版本 / 设备：
- 平台：Flutter

## 排查过程

1. 检查初始化时机 → 发现ContactPage在IMKitClient.init之前被创建
2. 检查初始化次数 → 发现初始化被调用两次
3. 检查登录流程 → 发现页面在登录成功前就加载了好友列表
4. 验证修复方案 → 将IMKitClient.init提前到登录页打开时执行

## 问题原因

ContactProvider注册时机问题，页面在IMKitClient.init完成前就加载了通讯录页面，导致依赖注入失败

## 解决方案

将IMKitClient.init提前到登录页面打开时执行，确保在加载ContactPage之前完成UIKit初始化

## 其他触发场景

