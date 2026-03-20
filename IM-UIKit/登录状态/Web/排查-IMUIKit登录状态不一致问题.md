---
track_type: 排查类
sub_type: 使用问题
product: IM-UIKit
feature: 登录状态
platform: Web
title: IMUIKit登录状态不一致问题
root_cause: 多次实例化/登录导致状态不一致
solution: 避免多次实例化和登录，确保IM实例和UIKit使用同一状态源
customers: ["河南潮生网络科技有限公司"]
source: chat_history
tags: ["IMUIKit", "登录状态", "Web", "状态不一致"]
created: 2025-11-04
updated: 2026-03-20
---

## 问题：Web IMUIKit登录状态不一致问题

## 问题详情

**现象**：
客户反馈已监听登录状态为已登录，但IMUIKit renderImDisConnected仍执行。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客户反馈登录状态监听正常但UI显示断开
2. 检查日志发现状态从2到1变化
3. 发现kitui仓库状态和im实例状态不一致

**关键发现**：

## 问题原因

多次实例化/登录导致状态不一致

## 解决方案

避免多次实例化和登录，确保IM实例和UIKit使用同一状态源

## 其他触发场景

