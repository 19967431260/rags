---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 登录
platform: iOS
title: 静态token登录返回403错误
root_cause: 应用配置了第三方回调登录方式，但用户使用静态token登录，会被系统禁止
solution: 使用第三方回调登录方式登录，参考文档：https://doc.yunxin.163.com/messaging/guide/TU3MTM2ODM?platform=iOS
customers: ['即客']
source: chat_history
tags: ['403', '登录', '静态token', '第三方回调']
created: 2025-01-21
updated: 2026-03-23
---

## 问题：iOS 静态token登录返回403错误

## 问题详情

**现象**：
iOS SDK登录返回403错误，用户状态正常但无法登录。

## 排查过程

1. 客户反馈iOS登录返回403
2. 查询发现用户一直使用静态token登录
3. 确认应用配置了第三方回调登录方式

## 问题原因

应用配置了第三方回调登录方式，但用户使用静态token登录，会被系统禁止

## 解决方案

使用第三方回调登录方式登录，参考文档：https://doc.yunxin.163.com/messaging/guide/TU3MTM2ODM?platform=iOS

## 其他触发场景

（合并时在此处追加）
