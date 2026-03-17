---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息推送
platform: iOS
title: Web端发消息iOS端无推送
root_cause: APNs证书配置异常，导致苹果推送服务器拒绝连接
solution: 在网易云信管理后台删除现有APNs证书，重新上传正确的生产正式证书，确保证书有效且与应用Bundle ID匹配
customers: ["北京北拓云鹰科技有限公司"]
source: chat_history
tags: ["iOS推送", "APNs", "BadDeviceToken", "证书配置", "离线推送"]
created: 2026-02-06
updated: 2026-03-17
---

## 问题：iOS Web端发消息iOS端无推送

## 问题详情

**现象**：
Web端作为发送端给iOS移动端发送消息时，iOS端退后台或杀死进程后无法收到推送通知，但手机之间发送消息有推送。

## 排查过程

1. 检查消息推送配置 → 查看消息payload配置
2. 查看服务端日志 → 发现报错APNS_HTTP2_PUSH_FAIL: Stream closed before a reply was received
3. 判断为证书信息异常，建议删除证书重新配置
4. 重新上传证书后仍失败 → 报错BadDeviceToken
5. 客户重新上传证书 → 推送成功

**关键发现**：苹果服务器拒绝连接，证书配置异常导致

## 问题原因

APNs证书配置异常，导致苹果推送服务器拒绝连接

## 解决方案

在网易云信管理后台删除现有APNs证书，重新上传正确的生产正式证书，确保证书有效且与应用Bundle ID匹配

## 其他触发场景
