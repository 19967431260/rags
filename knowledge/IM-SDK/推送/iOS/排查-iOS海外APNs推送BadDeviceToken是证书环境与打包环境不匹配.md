---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 推送
platform: iOS
title: iOS海外APNs推送BadDeviceToken是证书环境与打包环境不匹配
root_cause: 海外版iOS应用打包时使用了测试环境（Sandbox）的APNs证书，而生产环境推送走的是正式APNs服务器，导致BadDeviceToken错误
solution: iOS APNs推送BadDeviceToken解决：1.确认Xcode打包环境和配置的APNs证书环境（生产/开发）是否匹配；2.海外版应用需配置海外的APNs证书；3.检查Bundle ID是否与证书一致
customers: ["深圳市掌娱炫动"]
source: chat_history
tags: ["APNs","BadDeviceToken","iOS推送","证书环境","海外版"]
created: 2025-08-20
updated: 2026-03-26
---

## 问题：iOS iOS海外APNs推送BadDeviceToken是证书环境与打包环境不匹配

## 问题详情

**现象**：
国内版iOS应用APNs推送正常，国外版iOS用户收不到推送。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：iOS，海外版应用
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
rejectionReason=BadDeviceToken

## 排查过程

1. 客户提供accid、appkey和时间点 → 收集到关键信息
2. 客服查日志发现rejectionReason=BadDeviceToken → 确认是token校验失败
3. 确认是打包环境与配置的APNs证书环境不匹配 → 定位到根因
4. 客户确认使用了测试环境证书打包正式版应用 → 问题根因确认

**关键发现**：打包环境与APNs证书环境不匹配导致BadDeviceToken错误

## 问题原因

海外版iOS应用打包时使用了测试环境（Sandbox）的APNs证书，而生产环境推送走的是正式APNs服务器，导致BadDeviceToken错误

## 解决方案

iOS APNs推送BadDeviceToken解决：
1. 确认Xcode打包环境和配置的APNs证书环境（生产/开发）是否匹配
2. 海外版应用需配置海外的APNs证书
3. 检查Bundle ID是否与证书一致

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
