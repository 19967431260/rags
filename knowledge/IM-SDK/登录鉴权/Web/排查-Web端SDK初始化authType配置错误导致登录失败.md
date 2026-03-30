---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 登录鉴权
platform: Web
title: Web端SDK初始化authType配置错误导致登录失败
root_cause: Web SDK初始化时传入的authType参数与实际登录token类型不匹配；demo默认使用静态token，客户使用动态token但未修改authType配置
solution: 在SDK初始化配置中将authType设置为V2NIMLoginAuthType.V2NIM_LOGIN_AUTH_TYPE_DYNAMIC_TOKEN，与动态token方式匹配
customers: ["四川巨蟹科技有限公司"]
source: chat_history
tags: ["authType","动态token","初始化","登录","V2NIMLoginAuthType"]
created: 2025-08-08
updated: 2026-03-26
---

## 问题：Web Web端SDK初始化authType配置错误导致登录失败

## 问题详情

**现象**：
Web端（Uniapp编译到iOS）集成SDK，使用动态token登录方式时报错'密码错误'。

**复现步骤**：
（无明确步骤，从会话提取）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：Web端（Uniapp编译到iOS）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

客服确认demo中使用静态鉴权类型，客户使用动态token但demo中鉴权类型未同步修改 → 根因确认

**关键发现**：Web SDK初始化时传入的authType参数与实际登录token类型不匹配；demo默认使用静态token，客户使用动态token但未修改authType配置

## 问题原因

Web SDK初始化时传入的authType参数与实际登录token类型不匹配；demo默认使用静态token，客户使用动态token但未修改authType配置。

## 解决方案

在SDK初始化配置中将authType设置为V2NIMLoginAuthType.V2NIM_LOGIN_AUTH_TYPE_DYNAMIC_TOKEN，与动态token方式匹配。

## 其他触发场景

（合并时在此处追加）
