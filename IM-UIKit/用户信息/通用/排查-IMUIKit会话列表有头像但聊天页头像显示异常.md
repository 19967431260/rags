---
track_type: 排查类
sub_type: 测试问题
product: IM-UIKit
feature: 用户信息
platform: 通用
title: IM UIKit会话列表有头像但聊天页头像显示异常
root_cause: setUserInfoDelegate被空实现，导致获取用户信息失败，聊天页头像无法显示
solution: 检查并正确实现setUserInfoDelegate回调，不要空实现或遗漏实现。确保在回调中正确返回用户头像信息。
customers: []
source: chat_history
tags: ["setUserInfoDelegate", "头像显示", "UIKit", "Android"]
created: 2025-08-08
updated: 2025-08-08
---

## 问题：通用 IM UIKit会话列表有头像但聊天页头像显示异常

## 问题详情

**现象**：
客户反馈：会话列表有头像，但进入聊天页后头像显示不了。iOS正常，Android端收发消息正常。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：Android
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客服确认iOS正常，Android聊天页头像不显示 → 确认平台差异
2. 建议用demo源码工程配置登录信息测试复现 → 提供排查方向
3. 客户用demo源码配置后正常 → 定位为接入问题

**关键发现**：setUserInfoDelegate被空实现，导致获取用户信息失败，聊天页头像无法显示

## 问题原因

setUserInfoDelegate被空实现，导致获取用户信息失败，聊天页头像无法显示

## 解决方案

检查并正确实现setUserInfoDelegate回调，不要空实现或遗漏实现。确保在回调中正确返回用户头像信息。

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
