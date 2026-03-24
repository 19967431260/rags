---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 推送
platform: Android
title: Android端vivo推送SDK版本不兼容
root_cause: IM SDK 9.6.3版本与vivo推送SDK 4.0.0.0版本不兼容
solution: 升级到IM SDK 9.19.4版本，该版本支持vivo推送SDK 4.0.0.0；或降低vivo推送SDK版本
customers: ['北京睿圣网络科技有限公司']
source: chat_history
tags: ['vivo推送', 'SDK版本', '推送', 'Android', '9.6.3', '9.19.4']
created: 2025-01-13
updated: 2026-03-23
---

## 问题：Android Android端vivo推送SDK版本不兼容

## 问题详情

**现象**：
客户使用IM SDK 9.6.3版本，vivo推送SDK 4.0.0.0版本，出现推送类找不到的问题。

## 排查过程

1. 确认vivo推送SDK版本为4.0.0.0 → 发现版本不兼容\n2. 建议升级到IM SDK 9.19.4版本或降低推送SDK版本

## 问题原因

IM SDK 9.6.3版本与vivo推送SDK 4.0.0.0版本不兼容

## 解决方案

升级到IM SDK 9.19.4版本，该版本支持vivo推送SDK 4.0.0.0；或降低vivo推送SDK版本

## 其他触发场景

（合并时在此处追加）
