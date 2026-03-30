---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 账号管理
platform: iOS
title: iOS登录提示账号被封禁
root_cause: 账号被封禁导致无法登录，与平台无关（iOS和安卓应该都无法登录，可能是测试账号不同）
solution: 调用服务端接口解禁账号，参考文档：https://doc.yunxin.163.com/messaging2/server-apis/TIxMzI4MjE?platform=server
customers: ["江远装饰工程（天津）有限公司"]
source: chat_history
tags: ["iOS", "登录", "封禁", "解禁", "102422"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：iOS登录提示账号被封禁

## 问题详情

**现象**：
客户反馈iOS端登录提示账号被封禁，但安卓端可以正常登录，错误码102422。

**环境信息**：
- 平台：iOS

## 排查过程

1. 确认账号状态 → 日志中account为ceshi，确实被封禁
2. 提供解禁方案 → 提供服务端解禁接口文档

## 根因分析

账号被封禁导致无法登录，与平台无关（iOS和安卓应该都无法登录，可能是测试账号不同）

## 解决方案

调用服务端接口解禁账号，参考文档：https://doc.yunxin.163.com/messaging2/server-apis/TIxMzI4MjE?platform=server

## 其他触发场景

（无）
