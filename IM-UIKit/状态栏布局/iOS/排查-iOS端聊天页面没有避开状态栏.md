---
track_type: 排查类
sub_type: 集成类
product: IM-UIKit
feature: 状态栏布局
platform: iOS
title: iOS端聊天页面没有避开状态栏
root_cause: 新建iOS项目使用默认窗口模式(多窗口)，而NEUIKit的statusBarHeight获取方式（UIApplication.shared.statusBarFrame.height）在多窗口场景下返回0，未适配多窗口
solution: 方案1：删除Scene配置改回单窗口模式；方案2（推荐）：等待SDK下个版本适配多窗口。如需紧急解决可自行适配：使用UIWindowScene获取状态栏高度。
customers: ["南京锦辰文化传播有限公司"]
source: chat_history
tags: ["iOS", "状态栏", "安全区域", "UIWindowScene", "多窗口"]
created: 2025-08-26
updated: 2026-03-26
---

## 问题：iOS iOS端聊天页面没有避开状态栏

## 问题详情

**现象**：
客户接入iOS端UIKit后，会话列表和设置页面有头像，但聊天页面没有避开状态栏，从状态栏顶部开始布局。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：iOS
- 其他：新建iOS项目使用多窗口模式

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. demo正常但接入自己的app后有问题 → 确认是接入问题
2. 使用自己的navigatectrontroller → 确认自定义导航栏
3. 检查安全区域配置 → 检查布局配置
4. 发现是iOS多窗口适配问题 → 定位根本原因

**关键发现**：新建iOS项目使用默认窗口模式(多窗口)，而NEUIKit的statusBarHeight获取方式在多窗口场景下返回0

## 问题原因

新建iOS项目使用默认窗口模式(多窗口)，而NEUIKit的statusBarHeight获取方式（UIApplication.shared.statusBarFrame.height）在多窗口场景下返回0，未适配多窗口

## 解决方案

方案1：删除Scene配置改回单窗口模式；方案2（推荐）：等待SDK下个版本适配多窗口。如需紧急解决可自行适配：使用UIWindowScene获取状态栏高度。

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
