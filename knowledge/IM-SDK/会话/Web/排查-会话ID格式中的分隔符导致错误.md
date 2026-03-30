---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 会话
platform: Web
title: 会话ID格式中的分隔符导致错误
root_cause: 会话ID格式中包含了分隔符，需要去掉竖线。
solution: 正确格式："accid|2|teamId"（竖线前无空格）；如果看到receiverId为"|459..."说明分隔符处理有问题。
customers: ["仁人数字化科技（山东）有限公司"]
source: chat_history
tags: ["会话ID", "分隔符", "竖线", "Web"]
created: 2025-08-08
updated: 2026-03-26
---

## 问题：Web 会话ID格式中的分隔符导致错误

## 问题详情

**现象**：
会话ID格式中的分隔符导致错误。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：Web端
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

**关键发现**：会话ID格式中包含了分隔符，需要去掉竖线

## 问题原因

会话ID格式中包含了分隔符，需要去掉竖线。

## 解决方案

正确格式："accid|2|teamId"（竖线前无空格）；如果看到receiverId为"|459..."说明分隔符处理有问题。

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
