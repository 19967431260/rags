---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 登录
platform: Android
title: IM登录后经常断开问题
root_cause: 1. 同端互踢配置导致多设备登录冲突
2. 重复调用登录接口导致db关闭
solution: 1. 关闭同端互踢或更换测试账号
2. 使用自动登录而非重复调用手动登录
3. 参考文档：https://doc.yunxin.163.com/messaging/guide/TI1MTU1NDc?platform=android
customers: ["江西闪招信息技术有限公司"]
source: chat_history
tags: ["登录", "断开", "同端互踢", "自动登录", "Android"]
created: 2025-02-15
updated: 2026-03-20
---

## 问题：Android IM登录后经常断开问题

## 问题详情

**现象**：
Android端IM登录成功后经常退出登录，偶现问题。

## 排查过程

1. 检查日志发现开启了同端互踢配置
2. 发现iOS端也在登录同一账号，导致Android被踢下线
3. 后续排查发现重复登录导致本地db关闭

## 问题原因

1. 同端互踢配置导致多设备登录冲突
2. 重复调用登录接口导致db关闭

## 解决方案

1. 关闭同端互踢或更换测试账号
2. 使用自动登录而非重复调用手动登录
3. 参考文档：https://doc.yunxin.163.com/messaging/guide/TI1MTU1NDc?platform=android

## 其他触发场景

