---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 登录鉴权
platform: Web
title: Web端SDK和UIKit重复初始化导致呼叫accept失败
root_cause: SDK在多个Vue页面中重复初始化，导致内存中SDK状态异常。接听页面初始化后状态被覆盖，再展示callVideo页面时状态已混乱。
solution: SDK初始化（IM初始化和UIKit初始化）只放在App.vue中全局执行一次，不要在多个页面分别初始化
customers: ["山东铂明网络科技有限公司"]
source: chat_history
tags: ["初始化","accept","NECallEngine","重复初始化","Web","Vue"]
created: 2025-08-13
updated: 2026-03-26
---

## 问题：Web Web端SDK和UIKit重复初始化导致呼叫accept失败

## 问题详情

**现象**：
Web端集成呼叫组件，收到呼叫邀请后点击accept按钮时报错NECallEngine accept failed: not be call。

**复现步骤**：
（无明确步骤，从会话提取）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：Web
- 其他：Vue + 呼叫组件

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 排查发现在接听页面（callVideo.vue）和发起页面都进行了SDK初始化 → 定位问题
2. 导致内存中SDK状态异常 → 根因确认
3. 客服远程排查确认是重复初始化问题 → 确认

**关键发现**：SDK在多个Vue页面中重复初始化，导致内存中SDK状态异常。接听页面初始化后状态被覆盖，再展示callVideo页面时状态已混乱。

## 问题原因

SDK在多个Vue页面中重复初始化，导致内存中SDK状态异常。接听页面初始化后状态被覆盖，再展示callVideo页面时状态已混乱。

## 解决方案

SDK初始化（IM初始化和UIKit初始化）只放在App.vue中全局执行一次，不要在多个页面分别初始化。

## 其他触发场景

（合并时在此处追加）
