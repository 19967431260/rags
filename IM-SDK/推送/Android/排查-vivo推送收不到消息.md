---
track_type: 排查类
sub_type: 配置开通咨询
product: IM-SDK
feature: 推送
platform: Android
title: vivo推送收不到消息
root_cause: vivo SDK版本过低，IM适配的vivo推送sdk版本是v4.0.4.0_504。
solution: 1. 使用vivo_pushSDK_v4.0.4.0_504版本；2. 确保所有SDK版本号一致；3. vivo推送向下兼容做的不太好，需要使用指定版本。
customers: ["VIP云信-天天新鲜电子商务有限公司"]
source: chat_history
tags: ["vivo推送", "SDK版本", "Android", "离线推送"]
created: 2025-11-17
updated: 2026-03-20
---

## 问题：Android vivo推送收不到消息

## 问题详情

**现象**：
给vivo手机发送离线消息，vivo收不到消息，vivo开发后台也没有推送数量。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 检查vivo推送证书配置；2. 检查vivo SDK版本；3. 确认接收方是否在线。

**关键发现**：

## 问题原因

vivo SDK版本过低，IM适配的vivo推送sdk版本是v4.0.4.0_504。

## 解决方案

1. 使用vivo_pushSDK_v4.0.4.0_504版本；2. 确保所有SDK版本号一致；3. vivo推送向下兼容做的不太好，需要使用指定版本。

## 其他触发场景

