---
track_type: 排查类
sub_type: 集成类
product: 网易会议
feature: 虚拟背景
platform: Android
title: Android端设置内置虚拟背景列表后get时JSONArray转换异常
root_cause: NESettingsService里的设置接口默认与账号绑定，在登录之前调用时用户上下文未建立，导致数据存储和读取出现问题；需要在登录成功之后再调用setBuiltinVirtualBackgrounds
solution: 将setBuiltinVirtualBackgrounds的调用时机从'SDK初始化成功后'改为'用户登录成功之后'；在登录回调中执行设置操作
customers: ["四川捷登科技有限公司"]
source: chat_history
tags: ["虚拟背景","setBuiltinVirtualBackgrounds","Android","登录","NESettingsService","JSONArray"]
created: 2025-08-01
updated: 2026-03-26
---

## 问题：Android Android端设置内置虚拟背景列表后get时JSONArray转换异常

## 问题详情

**现象**：
Android端集成会议SDK，在初始化成功后调用setBuiltinVirtualBackgrounds设置内置虚拟背景图片（从apk资源复制到本地目录），再调用getBuiltinVirtualBackgrounds时报JSON Array类型转换异常。

**复现步骤**：
（无明确步骤，从会话提取）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 确认调用setBuiltinVirtualBackgrounds后设置生效，但get时异常 → 确认问题
2. 检查调用时机：在初始化成功后、登录之前调用 → 定位调用时机
3. 确认是set时机问题：必须在用户登录之后再设置 → 根因确认

**关键发现**：NESettingsService里的设置接口默认与账号绑定，在登录之前调用时用户上下文未建立，导致数据存储和读取出现问题；需要在登录成功之后再调用setBuiltinVirtualBackgrounds

## 问题原因

NESettingsService里的设置接口默认与账号绑定，在登录之前调用时用户上下文未建立，导致数据存储和读取出现问题；需要在登录成功之后再调用setBuiltinVirtualBackgrounds。

## 解决方案

将setBuiltinVirtualBackgrounds的调用时机从'SDK初始化成功后'改为'用户登录成功之后'；在登录回调中执行设置操作。

## 其他触发场景

（合并时在此处追加）
