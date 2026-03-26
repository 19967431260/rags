---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息
platform: iOS
title: 表情在YYLabel无法显示
root_cause: YYLabel 对 NSAttributedString 的处理方式与普通 UILabel 不兼容，导致表情富文本无法正确渲染
solution: 如需在 YYLabel 上显示表情，考虑修改表情解析源码使其兼容 YYLabel，或使用普通 UITextView 代替 YYLabel。SDK 返回的富文本本身没有问题。
customers: ["爱追光"]
source: chat_history
tags: ["YYLabel","表情","NEEmotionTool","UILabel","iOS"]
created: 2025-08-18
updated: 2026-03-26
---

## 问题：iOS 表情在YYLabel无法显示

## 问题详情

**现象**：
客户使用云信 SDK 的聊天表情，NEEmotionTool.getAttWithStr 方法在 YYLabel 上无法显示表情，但用普通 UILabel 可以显示。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客服确认返回值正常 → SDK返回正常
2. 客户确认 YYLabel 不支持，UILabel 可以 → 第三方库兼容性问题
3. 客户决定修改源码方法解决 → 自行解决

**关键发现**：YYLabel 对 NSAttributedString 的处理方式与普通 UILabel 不兼容，导致表情富文本无法正确渲染

## 问题原因

YYLabel 对 NSAttributedString 的处理方式与普通 UILabel 不兼容，导致表情富文本无法正确渲染

## 解决方案

如需在 YYLabel 上显示表情，考虑修改表情解析源码使其兼容 YYLabel，或使用普通 UITextView 代替 YYLabel。SDK 返回的富文本本身没有问题。

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
