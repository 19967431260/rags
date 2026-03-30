---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 登录
platform: Android
title: Android SDK登录414错误码PWD_ERROR为密码错误
root_cause: Android端SDK登录414错误：日志中显示PWD_ERROR（密码错误）；可能是appkey未正确设置导致密码校验失败
solution: Android SDK登录414 PWD_ERROR解决方法：1.确认密码/token正确性；2.检查appkey是否正确配置（appkey不打印敏感词，可搜索关键字定位）；3.token不打印以保护敏感信息
customers: ["杭州小众圈科技-诗音&回音"]
source: chat_history
tags: ["414","PWD_ERROR","Android","登录失败"]
created: 2025-08-13
updated: 2026-03-26
---

## 问题：Android Android SDK登录414错误码PWD_ERROR为密码错误

## 问题详情

**现象**：
Android端SDK登录报414错误码。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：Android
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客户提供错误截图 → 确认问题
2. 客服查日志确认PWD_ERROR → 确认密码错误
3. 密码错误 → 确认根因
4. appkey可能未正确设置 → 提供可能原因

**关键发现**：Android端SDK登录414错误日志显示PWD_ERROR（密码错误）

## 问题原因

Android端SDK登录414错误：日志中显示PWD_ERROR（密码错误）；可能是appkey未正确设置导致密码校验失败

## 解决方案

Android SDK登录414 PWD_ERROR解决方法：
1. 确认密码/token正确性
2. 检查appkey是否正确配置（appkey不打印敏感词，可搜索关键字定位）
3. token不打印以保护敏感信息

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
