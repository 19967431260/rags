---
track_type: 排查类
sub_type: 集成类
product: IM-UIKit
feature: Demo配置
platform: Android
title: IM UIKit Demo登录注册无反应
root_cause: 
solution: 需要修改三个配置：1. app/src/main/AndroidManifest.xml中的appkey；2. app/build.gradle中的applicationId；3. 登录页面的账号密码
customers: ["河北家和康孕"]
source: chat_history
tags: ["Demo", "登录", "配置", "UIKit"]
created: 2025-02-10
updated: 2026-03-20
---

## 问题：Android IM UIKit Demo登录注册无反应

## 问题详情

**现象**：
客户下载demo后运行，点击登录注册没有反应。

## 排查过程

（从会话记录提取）

## 问题原因

（详见上述排查过程）

## 解决方案

需要修改三个配置：1. app/src/main/AndroidManifest.xml中的appkey；2. app/build.gradle中的applicationId；3. 登录页面的账号密码

## 其他触发场景

