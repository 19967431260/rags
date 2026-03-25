---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息展示
platform: Windows
title: PC端图片无法显示
root_cause: Windows demo的预览功能实现问题，demo仅为基础演示不建议直接上线
solution: PC端预览是UI上层实现，建议基于项目自行检查实现，不建议直接使用demo上线
customers: ["COOLSHOW PTE.LTD."]
source: chat_history
tags: ["PC端", "图片显示", "Windows", "demo"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：PC端图片无法显示

## 问题详情

**现象**：
PC端聊天界面图片无法显示，但手机端查看正常

**环境信息**：
- 平台：Windows

## 排查过程

1. 检查消息ID → 客户无法提供\n2. 确认手机端正常 → 说明图片消息本身没问题\n3. 检查PC端实现 → 客户使用Windows demo\n4. 分析原因 → demo预览功能问题

## 根因分析

Windows demo的预览功能实现问题，demo仅为基础演示不建议直接上线

## 解决方案

PC端预览是UI上层实现，建议基于项目自行检查实现，不建议直接使用demo上线

## 其他触发场景

（无）
