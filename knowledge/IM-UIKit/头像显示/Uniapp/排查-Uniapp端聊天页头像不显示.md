---
track_type: 排查类
sub_type: 使用问题
product: IM-UIKit
feature: 头像显示
platform: Uniapp
title: Uniapp端聊天页头像不显示
root_cause: setUserInfoDelegate被设为空实现，导致聊天页无法获取用户头像信息。
solution: 对setUserInfoDelegate进行正确实现，而非空实现，即可正常显示聊天页头像。
customers: ["浙江闪铸集团有限公司", "珠海市纽带信息服务有限公司"]
source: chat_history
tags: ["setUserInfoDelegate", "头像显示", "Uniapp", "V10"]
created: 2025-08-08
updated: 2026-03-26
---

## 问题：Uniapp Uniapp端聊天页头像不显示

## 问题详情

**现象**：
客户使用Uniapp集成IM V10，会话列表头像显示正常但聊天页头像无法显示，收发消息功能正常。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：IM V10
- 系统版本 / 设备：Uniapp
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客户反馈会话列表有头像，聊天页头像显示不了 → 确认现象
2. 支持询问是否换过key测试（im功能试用已关闭）→ 排除key问题
3. 客户确认iOS头像正常 → 确认是Uniapp接入问题
4. 支持建议用demo源码工程配置登录信息测试 → 提供排查方向
5. 客户测试后确认是setUserInfoDelegate空实现导致 → 定位根因

**关键发现**：setUserInfoDelegate被设为空实现，导致聊天页无法获取用户头像信息

## 问题原因

setUserInfoDelegate被设为空实现，导致聊天页无法获取用户头像信息。

## 解决方案

对setUserInfoDelegate进行正确实现，而非空实现，即可正常显示聊天页头像。

## 其他触发场景

- [Uniapp] Uniapp端聊天页头像不显示，来源：珠海市纽带信息服务有限公司，2026-03-26
