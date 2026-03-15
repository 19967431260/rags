---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 隐私合规
platform: Android
title: 小米应用商店隐私审核-用户同意前获取IP地址
root_cause: 旧版本SDK在初始化时会监听网络变化，触发IP地址获取，违反隐私合规要求。
solution: 1. 升级SDK到最新版本9.21.10
2. 设置options.disableAwake = true关闭应用内自启动行为
3. 确保在用户同意隐私政策后再执行SDK初始化
customers: ["VIP云信-去狮城科技"]
source: chat_history
tags: ["隐私合规", "小米审核", "IP获取", "disableAwake", "NetworkListenerHelper"]
created: 2026-02-13
updated: 2026-03-15
---

## 问题：Android 小米应用商店隐私审核-用户同意前获取IP地址

## 问题详情

**现象**：
小米平台审核时检测到在用户同意隐私政策前，SDK通过NetworkListenerHelper获取了IP地址，导致应用被拒。堆栈显示com.netease.nimlib.network.g$a.onLinkPropertiesChanged触发了IP获取。

## 排查过程

1. 按照隐私合规文档调整 → 仍被拒
2. SDK版本9.19.10 → 升级到9.21.10
3. 设置disableAwake=true → 审核通过

## 问题原因

旧版本SDK在初始化时会监听网络变化，触发IP地址获取，违反隐私合规要求。

## 解决方案

1. 升级SDK到最新版本9.21.10
2. 设置options.disableAwake = true关闭应用内自启动行为
3. 确保在用户同意隐私政策后再执行SDK初始化
