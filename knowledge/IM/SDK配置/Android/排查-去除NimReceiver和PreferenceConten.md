---
track_type: 排查类
sub_type: 使用问题
product: IM
feature: SDK配置
platform: Android
title: 去除NimReceiver和PreferenceContentProvider自启动
root_cause: SDK版本过低（9.1.1），PreferenceContentProvider无法通过配置禁用
solution: 升级SDK到9.21.0最新版，配置disableawake为true。如果使用了UIKit且无法升级，可以单独升级IMSDK到最新版，SDK向下兼容
customers:
- 浙江甬润
source: chat_history
tags:
- 自启动
- NimReceiver
- PreferenceContentProvider
- disableawake
- 进程拉活
created: '2026-01-12'
updated: '2026-03-15'
---

## 问题：Android 去除NimReceiver和PreferenceContentProvider自启动

## 问题详情

**现象**：
客户反馈IM SDK存在开机自启动和进程间互相拉活问题，影响应用市场审核。使用SDK版本9.1.1

## 排查过程

1. 按FAQ去除NimReceiver → 开机自启动解决
2. 仍有PreferenceContentProvider导致的进程拉活
3. 确认使用了UIKit且基于2022年4月版本

## 问题原因

SDK版本过低（9.1.1），PreferenceContentProvider无法通过配置禁用

## 解决方案

升级SDK到9.21.0最新版，配置disableawake为true。如果使用了UIKit且无法升级，可以单独升级IMSDK到最新版，SDK向下兼容
