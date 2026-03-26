---
track_type: 排查类
sub_type: 使用问题
product: 呼叫组件
feature: 头像显示
platform: iOS
title: iOS端呼叫组件头像http地址图片不显示
root_cause: iOS系统默认禁止加载HTTP协议的明文图片资源，需要使用HTTPS加密连接。
solution: 将头像图片的URL地址从http改为https，即可正常显示。
customers: ["东莞市仁众丽科技有限公司"]
source: chat_history
tags: ["头像","http","https","iOS","呼叫组件"]
created: 2025-08-19
updated: 2026-03-26
---

## 问题：iOS iOS端呼叫组件头像http地址图片不显示

## 问题详情

**现象**：
iOS端呼叫组件中对方头像显示不正常，换成https地址后正常显示。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 排查头像不显示原因 → 图片加载问题
2. 确认为图片地址协议问题 → 使用http而非https
3. 换成https图片地址后恢复正常 → 问题解决

**关键发现**：iOS系统默认禁止加载HTTP协议的明文图片资源，需要使用HTTPS加密连接。

## 问题原因

iOS系统默认禁止加载HTTP协议的明文图片资源，需要使用HTTPS加密连接。

## 解决方案

将头像图片的URL地址从http改为https，即可正常显示。

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
