---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 消息附件
platform: iOS
title: iOS本地网络权限弹窗为SDK固有行为
root_cause: 云信iOS SDK固有行为会触发Local Network权限弹窗（Bonjour相关），这是SDK用于探测网络环境的技术需求
solution: iOS本地网络弹窗：这是云信SDK的固有行为，无法去除；在App Store Connect回复审核时说明app需要使用本地网络权限用于与云信服务器的连接即可；参考：https://faq.yunxin.163.com/#KB0405
customers: ["数字传递"]
source: chat_history
tags: ["iOS","Local Network","Bonjour","App Store审核","权限弹窗"]
created: 2025-08-14
updated: 2026-03-26
---

## 问题：iOS iOS本地网络权限弹窗为SDK固有行为

## 问题详情

**现象**：
客户App提交AppStore时苹果审核反馈：app请求访问本地网络信息但未发现使用该功能的具体场景。

**复现步骤**：
（无明确步骤，从会话提取）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：iOS
- 其他：App Store审核

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客户提供苹果审核拒绝截图 → 确认问题
2. 客服确认iOS SDK确实会触发本地网络权限弹窗 → 确认SDK行为
3. 提供FAQ文档说明此为SDK固有行为 → 说明
4. 指引在App Store Connect回复中说明：app需要使用本地网络权限用于SDK与服务器的连接 → 解决方案

**关键发现**：云信iOS SDK固有行为会触发Local Network权限弹窗（Bonjour相关），这是SDK用于探测网络环境的技术需求

## 问题原因

云信iOS SDK固有行为会触发Local Network权限弹窗（Bonjour相关），这是SDK用于探测网络环境的技术需求。

## 解决方案

iOS本地网络弹窗：这是云信SDK的固有行为，无法去除；在App Store Connect回复审核时说明app需要使用本地网络权限用于与云信服务器的连接即可；参考：https://faq.yunxin.163.com/#KB0405

## 其他触发场景

（合并时在此处追加）
