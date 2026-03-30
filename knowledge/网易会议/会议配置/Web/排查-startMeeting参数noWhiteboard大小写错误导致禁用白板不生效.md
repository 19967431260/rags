---
track_type: 排查类
sub_type: 使用问题
product: 网易会议
feature: 会议配置
platform: Web
title: startMeeting参数noWhiteboard大小写错误导致禁用白板不生效
root_cause: 文档中参数名写成了noWhiteboard（大写B），但实际SDK要求的参数名是noWhiteboard（小写b），即noWhiteboard而非noWhiteboard
solution: 将noWhiteboard参数名改为noWhiteboard（小写b），修改后禁用白板功能正常；文档已同步修正
customers: ["云信-七七星球技术对接群"]
source: chat_history
tags: ["网易会议", "startMeeting", "noWhiteboard", "文档错误"]
created: 2025-08-12
updated: 2026-03-26
---

## 问题：Web startMeeting参数noWhiteboard大小写错误导致禁用白板不生效

## 问题详情

**现象**：
客户在Web端调用startMeeting时传入noWhiteboard参数想要禁用白板，但设置后进入会议仍然显示白板。SDK版本4.7.0。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：4.7.0
- 系统版本 / 设备：Web端
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客服确认参数传递方式 → 确认参数有传递
2. 客服验证确认noAudio生效但noWhiteboard不生效 → 排除参数传递问题
3. 客服排查SDK行为后发现：参数名中Board的b应为小写 → 定位参数名大小写问题

**关键发现**：文档中参数名写成了noWhiteboard（大写B），但实际SDK要求小写b

## 问题原因

文档中参数名写成了noWhiteboard（大写B），但实际SDK要求的参数名是noWhiteboard（小写b），即noWhiteboard而非noWhiteboard

## 解决方案

将noWhiteboard参数名改为noWhiteboard（小写b），修改后禁用白板功能正常；文档已同步修正

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
