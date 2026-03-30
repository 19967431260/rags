---
track_type: "排查类"
sub_type: "使用问题"
product: "IM-SDK"
feature: "隐私合规"
platform: "Android"
title: "隐私政策未同意前SDK初始化导致应用下架"
root_cause: "用户在同意隐私声明之前调用了SDK的init方法"
solution: "参考文档中的分步初始化，用户在同意隐私声明之前不要调用init方法。文档：https://doc.yunxin.163.com/messaging/guide/Tg3NDExMDA?platform=android"
customers: ["北京中科大洋"]
source: "chat_history"
tags: ["隐私合规", "初始化", "应用下架", "隐私政策"]
created: "2025-09-28"
updated: "2026-03-20"
---

## 问题：Android 隐私政策未同意前SDK初始化导致应用下架

## 问题详情

**现象**：
Android版本APP在应用市场审核被全网下架，理由是首次运行未经用户阅读并同意隐私政策，存在向第三方SDK通信的行为。

## 排查过程

1. 查看检测报告发现是网易云信SDK相关日志
2. 确认SDK版本为9.8.0
**关键发现**：用户在同意隐私声明之前调用了init方法

## 问题原因

用户在同意隐私声明之前调用了SDK的init方法

## 解决方案

参考文档中的分步初始化，用户在同意隐私声明之前不要调用init方法。文档：https://doc.yunxin.163.com/messaging/guide/Tg3NDExMDA?platform=android

## 其他触发场景
