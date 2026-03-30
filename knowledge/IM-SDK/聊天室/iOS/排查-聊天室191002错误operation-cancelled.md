---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 聊天室
platform: iOS
title: 聊天室191002错误operation cancelled
root_cause: 接口调用过于频繁，短时间内重复调用enter导致主动取消
solution: 检查业务逻辑，避免短时间内重复调用enter和exit，确保接口调用时序正确
customers: ["云信+乐次元"]
source: chat_history
tags: ["191002", "operation cancelled", "聊天室", "iOS", "重复登录"]
created: 2025-11-25
updated: 2026-03-20
---

## 问题：iOS 聊天室191002错误operation cancelled

## 问题详情

**现象**：
iOS端调用加入聊天室经常失败，错误代码191002，错误描述operation cancelled

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 用户提供报错信息和日志
2. 技术支持分析日志发现存在重复登录情况
3. 日志显示短时间内连续两次调用enter接口
4. 结论：接口调用太频繁，不停的enter和exit，enter两次调用导致状态回调多，看起来是不停重连

**关键发现**：

## 问题原因

接口调用过于频繁，短时间内重复调用enter导致主动取消

## 解决方案

检查业务逻辑，避免短时间内重复调用enter和exit，确保接口调用时序正确

## 其他触发场景

