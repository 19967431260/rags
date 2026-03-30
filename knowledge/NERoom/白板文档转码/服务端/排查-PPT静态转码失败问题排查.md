---
track_type: "排查类"
sub_type: "使用问题"
product: "NERoom"
feature: "白板/文档转码"
platform: "服务端"
title: "PPT静态转码失败问题排查"
root_cause: "静态转码功能对pptx格式兼容性存在问题"
solution: "临时方案：将pptx文件用本地office打开，另存为ppt格式后再上传转码；或等待后续优化版本"
customers: ["智慧树"]
source: "chat_history"
tags: ["转码失败", "pptx", "静态转码", "白板", "兼容性"]
created: "2025-09-03"
updated: "2026-03-20"
---

## 问题：服务端 PPT静态转码失败问题排查

## 问题详情

**现象**：
PPT文件静态转码失败，有时能成功有时失败，JPG和H5格式都有问题。部分pptx文件秒失败。

## 排查过程

1. 分析失败原因 → 静态转码功能兼容性问题
2. 对比不同格式 → pptx文件处理有问题，ppt格式正常
3. 临时解决方案 → 本地office另存为ppt格式后上传
**关键发现**：pptx格式兼容性存在问题

## 问题原因

静态转码功能对pptx格式兼容性存在问题

## 解决方案

临时方案：将pptx文件用本地office打开，另存为ppt格式后再上传转码；或等待后续优化版本

## 其他触发场景
