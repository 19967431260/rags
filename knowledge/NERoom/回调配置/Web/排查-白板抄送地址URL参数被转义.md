---
track_type: 排查类
sub_type: 使用问题
product: NERoom
feature: 回调配置
platform: Web
title: 白板抄送地址URL参数被转义
root_cause: 控制台输入框存在转义问题
solution: 已修复，可重新配置
customers: ["北京师范大学"]
source: chat_history
tags: ["白板", "抄送", "URL转义", "控制台"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：白板抄送地址URL参数被转义

## 问题详情

**现象**：
控制台配置白板回调地址时，&符号被转义为&amp;，导致地址不正确

**环境信息**：
- 平台：Web

## 排查过程

1. 确认输入框粘贴内容
2. 发现保存后参数被转义

## 根因分析

控制台输入框存在转义问题

## 解决方案

已修复，可重新配置

## 其他触发场景

（无）
