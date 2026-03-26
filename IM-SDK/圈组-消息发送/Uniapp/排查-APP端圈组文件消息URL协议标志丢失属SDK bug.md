---
track_type: 排查类
sub_type: 测试问题
product: IM-SDK
feature: 圈组-消息发送
platform: Uniapp
title: APP端圈组文件消息URL协议标志丢失属SDK bug
root_cause: APP端SDK在处理文件消息url时存在bug，导致协议标志（://）丢失，已确认并反馈给研发修复
solution: APP端圈组文件消息URL协议标志丢失是SDK bug：1.临时方案：将文件信息放在消息ext扩展字段里绕过；2.正式修复等待SDK版本更新；APP端上传图片后没有文件名和宽高信息也是SDK限制
customers: ["家有学霸"]
source: chat_history
tags: ["圈组","Uniapp","APP端","URL协议","文件消息","SDK bug"]
created: 2025-08-24
updated: 2026-03-26
---

## 问题：Uniapp APP端圈组文件消息URL协议标志丢失属SDK bug

## 问题详情

**现象**：
APP端圈组发送文件类消息时，attach的url中协议标志丢失（http://snim-nosdn.netease.im/xxx变成httpsnim-nosdn.netease.im/xxx，少了两个斜杠），网页端正常。

**复现步骤**：
（无明确步骤，从会话提取）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：APP端
- 其他：Uniapp + 圈组

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客户提供APP端和web端对比截图，APP端URL协议标志丢失 → 确认问题
2. 客服确认是SDK问题，已反馈给研发处理 → 确认根因
3. 临时方案：可尝试将文件信息放在ext扩展字段里绕过 → 临时方案

**关键发现**：APP端SDK在处理文件消息url时存在bug，导致协议标志（://）丢失，已确认并反馈给研发修复

## 问题原因

APP端SDK在处理文件消息url时存在bug，导致协议标志（://）丢失，已确认并反馈给研发修复。

## 解决方案

APP端圈组文件消息URL协议标志丢失是SDK bug：1.临时方案：将文件信息放在消息ext扩展字段里绕过；2.正式修复等待SDK版本更新；APP端上传图片后没有文件名和宽高信息也是SDK限制。

## 其他触发场景

（合并时在此处追加）
