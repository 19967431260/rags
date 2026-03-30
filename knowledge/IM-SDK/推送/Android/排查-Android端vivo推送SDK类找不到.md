---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 推送
platform: Android
title: Android端vivo推送SDK类找不到
root_cause: vivo推送SDK的aar文件未正确集成到项目中
solution: 下载并集成vivo_pushSDK_v3.0.0.4_484.aar文件
customers: ['北京睿圣网络科技有限公司']
source: chat_history
tags: ['vivo推送', 'NoClassDefFoundError', 'PushClient', 'Android', '集成']
created: 2025-01-14
updated: 2026-03-23
---

## 问题：Android Android端vivo推送SDK类找不到

## 问题详情

**现象**：
客户集成vivo推送SDK后出现NoClassDefFoundError，找不到PushClient类。

## 排查过程

1. 确认vivo推送SDK已集成 → 发现aar文件未正确引入\n2. 提供正确的vivo_pushSDK_v3.0.0.4_484.aar文件

## 问题原因

vivo推送SDK的aar文件未正确集成到项目中

## 解决方案

下载并集成vivo_pushSDK_v3.0.0.4_484.aar文件

## 其他触发场景

（合并时在此处追加）
