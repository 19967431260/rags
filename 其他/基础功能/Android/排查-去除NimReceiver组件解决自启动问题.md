---
track_type: 排查类
sub_type: 功能实现咨询
product: 其他
feature: 基础功能
platform: Android
title: 去除NimReceiver组件解决自启动问题
root_cause: ""
solution: "参考文档 https://faq.yunxin.163.com/#KB0493 配置，在AndroidManifest.xml中对com.netease.nimlib.service.NimReceiver添加tools:node=\"remove\"移除该组件，同时设置SDKOptions.disableAwake=true禁用自启动。"
customers:
  - 无锡农商
source: chat_history
tags:
  - 消息
created: "2025-06-13"
updated: "2025-06-13"
---

## 问题：Android去除NimReceiver组件解决自启动问题

## 问题详情

**现象**：
客户咨询如何去除 com.netease.nimlib.service.NimReceiver 组件以解决自启动检测问题。

**环境信息**：
- 平台：Android
- 涉及组件：NimReceiver、NIMContentProvider

## 排查过程

1. **问题确认** → 客户需要去除NimReceiver组件
   - 参考文档：https://faq.yunxin.163.com/#KB0493
   - 按照文档配置移除NimReceiver

2. **关联问题确认** → NIMContentProvider是否也需要处理
   - NIMContentProvider不会自启动，无需额外处理

3. **配置验证** → 确认SDK版本和配置参数
   - 检查SDKOptions.disableAwake设置

**关键发现**：需要同时配置AndroidManifest移除组件和SDK参数禁用自启动

## 问题原因

Android应用自启动检测会扫描应用中的Receiver组件，NimReceiver作为云信SDK的广播接收器可能被检测为自启动组件。

## 解决方案

1. **移除NimReceiver组件**：
   在AndroidManifest.xml中添加：
   ```xml
   <receiver android:name="com.netease.nimlib.service.NimReceiver" tools:node="remove"/>
   ```

2. **禁用SDK自启动**：
   初始化时设置SDKOptions参数：
   ```java
   SDKOptions options = new SDKOptions();
   options.disableAwake = true;
   ```
   参考文档：https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/classcom_1_1netease_1_1nimlib_1_1sdk_1_1_s_d_k_options.html

## 其他触发场景

