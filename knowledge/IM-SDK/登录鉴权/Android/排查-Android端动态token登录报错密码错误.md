---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 登录鉴权
platform: Android
title: Android端动态token登录报错密码错误
root_cause: demo中的鉴权类型默认是静态token，客户使用了动态token但demo中的鉴权类型未同步修改
solution: 将demo中的登录鉴权类型同步修改为V2NIMLoginAuthType.V2NIM_LOGIN_AUTH_TYPE_DYNAMIC_TOKEN动态token方式
customers: ["千寻代售APP沟通群"]
source: chat_history
tags: ["动态token","V2NIMLoginAuthType","登录","鉴权类型","密码错误"]
created: 2025-08-08
updated: 2026-03-26
---

## 问题：Android Android端动态token登录报错密码错误

## 问题详情

**现象**：
Android端使用V2NIMLoginAuthType.V2NIM_LOGIN_AUTH_TYPE_DYNAMIC_TOKEN动态token方式登录，但报密码错误。demo中是静态token方式。

**复现步骤**：
（无明确步骤，从会话提取）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

客服确认demo中使用的是静态鉴权类型，客户需将demo中的鉴权类型也改为动态token方式 → 解决方案明确

**关键发现**：demo中的鉴权类型默认是静态token，客户使用了动态token但demo中的鉴权类型未同步修改

## 问题原因

demo中的鉴权类型默认是静态token，客户使用了动态token但demo中的鉴权类型未同步修改。

## 解决方案

将demo中的登录鉴权类型同步修改为V2NIMLoginAuthType.V2NIM_LOGIN_AUTH_TYPE_DYNAMIC_TOKEN动态token方式。

## 其他触发场景

（合并时在此处追加）
