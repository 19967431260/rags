---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 离线推送
platform: Android
title: 荣耀推送403 accesstoken无效
root_cause: 荣耀控制台配置的证书信息有误，导致accesstoken无效
solution: 检查荣耀后台和云信后台的证书配置，确保各个字段正确。可以拿着token咨询荣耀客服确认哪个字段错误
customers: ["深圳市九町科技有限公司"]
source: chat_history
tags: ["403","荣耀推送","accesstoken","证书配置"]
created: 2026-02-08
updated: 2026-03-17
---

## 问题：Android 荣耀推送403 accesstoken无效

## 问题详情

**现象**：
荣耀推送注册成功，但APP划掉后收不到推送消息，推送报错403

## 排查过程

1. 检查token注册状态 → 注册成功
2. 查看推送日志 → 发现403错误
3. 分析错误原因 → 荣耀返回accesstoken无效

**关键发现**：荣耀服务器返回403，表示accesstoken没有权限

## 问题原因

荣耀控制台配置的证书信息有误，导致accesstoken无效

## 解决方案

检查荣耀后台和云信后台的证书配置，确保各个字段正确。可以拿着token咨询荣耀客服确认哪个字段错误

## 其他触发场景

