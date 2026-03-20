---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 登录
platform: Android
title: 同一AppKey不同accid登录一个成功一个失败302
root_cause: token生成或传递存在问题，导致其中一个accid使用的token无效。
solution: 1. 使用服务端接口重新刷新token；2. 保存入参和回参；3. 登录时打印所有参数进行对比排查。
customers: ["VIP云信-四创科技有限公司"]
source: chat_history
tags: ["登录", "302", "token", "Android", "静态token"]
created: 2025-11-28
updated: 2026-03-20
---

## 问题：Android 同一AppKey不同accid登录一个成功一个失败302

## 问题详情

**现象**：
同一AppKey下两个accid，使用token方式登录IM，一个可以登录成功，另一个提示账号密码错误，错误码302。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 确认两个accid使用相同登录方式；2. 服务端检查token生成接口返回；3. 对比两个accid的token值；4. 查看后台报错日志确认指向token问题。

**关键发现**：

## 问题原因

token生成或传递存在问题，导致其中一个accid使用的token无效。

## 解决方案

1. 使用服务端接口重新刷新token；2. 保存入参和回参；3. 登录时打印所有参数进行对比排查。

## 其他触发场景

