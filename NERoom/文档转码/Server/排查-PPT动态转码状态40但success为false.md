---
track_type: 排查类
sub_type: 使用问题
product: NERoom
feature: 文档转码
platform: Server
title: PPT动态转码状态40但success为false
root_cause: Linux上转码引擎对wmf图片解析存在问题
solution: 建议先转PDF再转码；转码引擎优化需到春节后
customers: ['智慧树']
source: chat_history
tags: ['PPT转码', 'wmf', '互动白板', '转码失败']
created: 2024-12-31
updated: 2026-03-23
---

## 问题：服务端 PPT动态转码状态40但success为false

## 问题详情

**现象**：
PPT转码返回状态40（成功），但thumbnailDto中success为false，页码也没有，导致异常。原因是转码引擎对wmf图片解析存在问题。

## 排查过程

1. 客户反馈PPT转码状态40但无页码 → 客服确认问题
2. 客户提供PPT文件复现 → 确认是Linux上对wmf图片解析存在问题
3. 反馈研发确认修复时间

## 问题原因

Linux上转码引擎对wmf图片解析存在问题

## 解决方案

建议先转PDF再转码；转码引擎优化需到春节后

## 其他触发场景

（合并时在此处追加）
