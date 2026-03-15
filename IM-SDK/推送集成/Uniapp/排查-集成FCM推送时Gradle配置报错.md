---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 推送集成
platform: Uniapp
title: 集成FCM推送时Gradle配置报错
root_cause: Gradle版本不支持plugins {}这种写法,或者plugins {}块放错了位置
solution: 将plugins {}语法改为apply plugin方式：apply plugin: 'com.android.application' 和 apply plugin: 'com.google.gms.google-services'
customers: ["北京北拓云鹰科技有限公司"]
source: chat_history
tags: ["FCM", "Gradle", "plugins", "google-services", "Uniapp"]
created: 2026-02-09
updated: 2026-03-15
---

## 问题：Uniapp 集成FCM推送时Gradle配置报错

## 问题详情

**现象**：
在Uniapp项目中集成谷歌FCM推送,按照文档在app/build.gradle中添加plugins {}块配置时报错。使用的是离线打包方式,需要配置Google Services插件。

## 排查过程

1. 用户在app/build.gradle中使用plugins {}语法添加com.google.gms.google-services插件时报错
2. 检查Gradle版本兼容性

**关键发现**：Gradle版本不支持plugins {}这种写法,或者plugins {}块放错了位置

## 问题原因

Gradle版本不支持plugins {}这种写法,或者plugins {}块放错了位置

## 解决方案

将plugins {}语法改为apply plugin方式：
```
apply plugin: 'com.android.application'
apply plugin: 'com.google.gms.google-services'
```

## 其他触发场景
