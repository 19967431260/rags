---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 登录
platform: Web
title: appkey blocked错误的解决方法
root_cause: 套餐被降级为免费版，导致动态token登录策略被关闭。
solution: 在云信控制台重新开启动态token登录策略即可。
customers: ["仁人数字化科技（山东）有限公司", "元拓科技（大连）有限公司"]
source: chat_history
tags: ["appkey blocked", "动态token", "登录策略", "套餐降级"]
created: 2025-08-08
updated: 2026-03-26
---

## 问题：Web appkey blocked错误的解决方法

## 问题详情

**现象**：
Web端登录失败，报appkey blocked错误。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：Web端
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
appkey blocked

## 排查过程

**关键发现**：套餐被降级为免费版，导致动态token登录策略被关闭

## 问题原因

套餐被降级为免费版，导致动态token登录策略被关闭。

## 解决方案

在云信控制台重新开启动态token登录策略即可。

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
