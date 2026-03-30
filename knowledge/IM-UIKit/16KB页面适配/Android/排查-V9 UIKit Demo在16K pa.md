---
track_type: 排查类
sub_type: 集成类
product: IM-UIKit
feature: 16KB页面适配
platform: Android
title: V9 UIKit Demo在16K page设备闪退
root_cause: 9.7.5版本内部库不适配16KB页面，且缺少alog日志库依赖
solution: 升级到9.7.6分支，并添加implementation("com.netease.yunxin.kit:alog:1.1.1")依赖
customers: ['北京美车天下科技']
source: chat_history
tags: ['16KB', 'Android', '闪退', 'UIKit', 'vivo']
created: 2025-09-15
updated: 2026-03-25
---

## 问题：Android V9 UIKit Demo在16K page设备闪退

## 问题详情

**现象**：
客户运行V9 UIKit Demo在16K page设备上闪退，vivo x200设备。

## 解决方案

升级到9.7.6分支，并添加implementation("com.netease.yunxin.kit:alog:1.1.1")依赖
