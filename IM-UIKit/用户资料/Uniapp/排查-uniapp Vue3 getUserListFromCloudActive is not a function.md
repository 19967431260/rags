---
track_type: 排查类
sub_type: 集成类
product: IM-UIKit
feature: 用户资料
platform: Uniapp
title: uniapp Vue3 getUserListFromCloudActive is not a function
root_cause: uniapp Vue3版本中UIKit的导入或初始化配置未正确处理。
solution: 按照文档导入UIKit源码依赖：https://doc.yunxin.163.com/messaging-uikit/guide/jgwMDI2NTU?platform=uniapp，确保正确处理导入和初始化配置。
customers: ["武汉毅麦信息科技有限公司"]
source: chat_history
tags: ["uniapp","Vue3","getUserListFromCloud","UIKit","初始化"]
created: 2025-08-06
updated: 2026-03-26
---

## 问题：Uniapp uniapp Vue3 getUserListFromCloudActive is not a function

## 问题详情

**现象**：
客户使用uniapp Vue3版本调用UIKit获取用户信息时报错：uni.$UIKitStore.userStore.getUserListFromCloudActive is not a function

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客服确认报错信息 → UIKit API 调用问题

**关键发现**：uniapp Vue3版本中UIKit的导入或初始化配置未正确处理。

## 问题原因

uniapp Vue3版本中UIKit的导入或初始化配置未正确处理。

## 解决方案

按照文档导入UIKit源码依赖：https://doc.yunxin.163.com/messaging-uikit/guide/jgwMDI2NTU?platform=uniapp，确保正确处理导入和初始化配置。

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
