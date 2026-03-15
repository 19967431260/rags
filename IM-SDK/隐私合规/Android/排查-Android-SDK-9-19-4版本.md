---
track_type: 排查类
sub_type: BUG问题
product: IM-SDK
feature: 隐私合规
platform: Android
title: Android SDK 9.19.4版本隐私合规问题-同意前获取IP
root_cause: SDK 9.19.4版本存在隐私合规问题，在用户同意隐私协议前会获取IP地址。
solution: 更新到最新版本SDK即可解决此隐私合规问题。
customers: ["智慧丘比特"]
source: chat_history
tags: ["Android", "隐私合规", "IP获取", "SDK版本"]
created: 2026-01-16
updated: 2026-03-15
---

## 问题：Android Android SDK 9.19.4版本隐私合规问题-同意前获取IP

## 问题详情

**现象**：
安卓市场检测发现在用户同意隐私协议前获取IP地址，调用堆栈显示是云信SDK在调用。SDK初始化已按照文档隐私合规方式进行。SDK版本9.19.4。

## 问题原因

SDK 9.19.4版本存在隐私合规问题，在用户同意隐私协议前会获取IP地址。

## 解决方案

更新到最新版本SDK即可解决此隐私合规问题。

## 其他触发场景

（合并时在此处追加）
- [Android] Android SDK 9.19.4版本隐私合规问题-同意前获取IP，来源：['智慧丘比特']，2026-03-15
