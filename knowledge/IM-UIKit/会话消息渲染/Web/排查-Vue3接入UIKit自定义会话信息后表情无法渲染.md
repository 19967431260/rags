---
track_type: 排查类
sub_type: 使用问题
product: IM-UIKit
feature: 会话消息渲染
platform: Web
title: Vue3接入UIKit自定义会话信息后表情无法渲染
root_cause: 业务层使用renderMessageOuterContent自定义渲染时，未解析文本中对应的emoji字符
solution: 使用renderMessageOuterContent自定义渲染时，需要解析文本中对应emoji的字符，映射到对应的emoji图标进行展示；可参考UIKit源码中的emoji映射关系
customers: ["上海奇已科技"]
source: chat_history
tags: ["emoji","渲染","Vue3","UIKit","renderMessageOuterContent"]
created: 2025-08-20
updated: 2026-03-26
---

## 问题：Web Vue3接入UIKit自定义会话信息后表情无法渲染

## 问题详情

**现象**：
Vue3接入UIKit实现Web在线聊天功能，自定义会话信息后发现表情无法渲染。客户使用renderMessageOuterContent自定义渲染消息体外层内容，传入SDK的消息内容中emoji字符未解析显示。

**复现步骤**：
（无明确步骤，从会话提取）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客户反馈Vue3接入UIKit自定义会话信息后表情无法渲染 → 确认为使用问题
2. 排查发现renderMessageOuterContent所有渲染逻辑走客户业务逻辑，传入SDK什么就显示什么 → 渲染逻辑不经过SDK内部处理
3. 对比源码emoji映射关系，业务层需要自行解析文本中emoji字符并映射到对应emoji图标进行展示 → 根因定位

**关键发现**：renderMessageOuterContent自定义渲染时，emoji字符的解析映射不经过SDK，需业务层自行处理

## 问题原因

业务层使用renderMessageOuterContent自定义渲染时，未解析文本中对应的emoji字符。

## 解决方案

使用renderMessageOuterContent自定义渲染时，需要解析文本中对应emoji的字符，映射到对应的emoji图标进行展示；可参考UIKit源码中的emoji映射关系。

## 其他触发场景

（合并时在此处追加）
