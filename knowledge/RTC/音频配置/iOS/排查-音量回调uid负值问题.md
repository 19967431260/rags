---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 音频配置
platform: iOS
title: 音量回调uid负值问题
root_cause: SDK版本过旧存在bug
solution: 升级SDK到最新版本5.8.21解决uid负值问题。纯音频版本5.6.50也可用。
customers: ["武汉语舟科技有限公司-dx"]
source: chat_history
tags: ["音量回调","uid","负值","SDK版本"]
created: 2025-06-12
updated: 2025-06-12
---

## 问题：iOS 音量回调uid负值问题

## 问题详情

**现象**：
客户设置音量回调，volumeArray中uid一直是负值。

## 排查过程

1. 检查SDK版本 → 检查版本
2. 发现使用5.4.1旧版本 → 发现问题
3. 升级到5.8.21后正常 → 解决问题

**关键发现**：SDK版本过旧存在bug

## 问题原因

SDK版本过旧存在bug

## 解决方案

升级SDK到最新版本5.8.21解决uid负值问题。纯音频版本5.6.50也可用。

## 其他触发场景

