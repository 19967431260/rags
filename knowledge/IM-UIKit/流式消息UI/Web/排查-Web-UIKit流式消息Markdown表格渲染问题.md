---
track_type: 排查类
sub_type: 使用问题
product: IM-UIKit
feature: 流式消息UI
platform: Web
title: Web UIKit流式消息Markdown表格渲染问题
root_cause: UIKit内部对AI数字人消息有特殊处理逻辑，会执行markdown解析和合并，普通流式消息不触发该逻辑。
solution: 1. 借鉴AI数字人消息的处理方式，对普通流式消息同样处理
2. 监听底层SDK的onReceiveMessages和onReceiveMessageModified回调
3. 参考文档：https://doc.yunxin.163.com/messaging2/guide/jg1NjE1NDY?platform=client
4. 使用NEMarkdownParser类解析文本消息内容
customers: ["淘酷"]
source: chat_history
tags: ["流式消息", "Markdown", "表格渲染", "UIKit", "Web", "数字人"]
created: 2025-11-24
updated: 2026-03-20
---

## 问题：Web Web UIKit流式消息Markdown表格渲染问题

## 问题详情

**现象**：
客户在使用Web UIKit展示流式消息时，发现服务端发送的Markdown表格格式无法正确渲染为表格样式，而是原内容展示。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 确认问题现象 → Markdown表格在网页可展示，但在聊天页面原内容展示
2. 分析UI处理逻辑 → UIKit默认只对AI数字人消息执行markdown解析
3. 检查消息类型 → 客户发送的是普通流式消息，非数字人消息
4. 提供解决方案 → 借鉴数字人处理方式处理普通流式消息
**关键发现**：UIKit只对数字人消息执行markdown合并处理，普通消息不走该逻辑

**关键发现**：

## 问题原因

UIKit内部对AI数字人消息有特殊处理逻辑，会执行markdown解析和合并，普通流式消息不触发该逻辑。

## 解决方案

1. 借鉴AI数字人消息的处理方式，对普通流式消息同样处理
2. 监听底层SDK的onReceiveMessages和onReceiveMessageModified回调
3. 参考文档：https://doc.yunxin.163.com/messaging2/guide/jg1NjE1NDY?platform=client
4. 使用NEMarkdownParser类解析文本消息内容

## 其他触发场景

