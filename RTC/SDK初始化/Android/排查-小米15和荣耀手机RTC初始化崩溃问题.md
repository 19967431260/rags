---
track_type: "排查类"
sub_type: "集成类"
product: "RTC"
feature: "SDK初始化"
platform: "Android"
title: "小米15和荣耀手机RTC初始化崩溃问题"
root_cause: "RTC SDK版本与Android 14/15新系统存在兼容性问题"
solution: "RTC SDK升级到4.6.67版本可解决。单独依赖nertc-base：implementation 'com.netease.yunxin:nertc-base:4.6.67'，去除nertc-full module。"
customers: ["ISV云信-龙软科技-音视频私有化"]
source: "chat_history"
tags: ["RTC", "初始化崩溃", "小米15", "荣耀", "Android 15", "4.6.67"]
created: "2025-09-15"
updated: "2026-03-20"
---

## 问题：Android 小米15和荣耀手机RTC初始化崩溃问题

## 问题详情

**现象**：
客户反馈：小米15和荣耀手机初始化会有崩溃情况，SDK一直用着没有升级，最近有新机型初始化闪退。崩溃堆栈显示在libnertc_sdk.so中。

## 排查过程

1. 客户提供崩溃堆栈信息
2. 技术支持查看堆栈发现是已知兼容性问题
3. 确认设备为小米15（Android 15）和荣耀（Android 14）
4. 查得是RTC SDK与Android新版本的兼容性问题

## 问题原因

RTC SDK版本与Android 14/15新系统存在兼容性问题

## 解决方案

RTC SDK升级到4.6.67版本可解决。单独依赖nertc-base：implementation 'com.netease.yunxin:nertc-base:4.6.67'，去除nertc-full module。

## 其他触发场景
