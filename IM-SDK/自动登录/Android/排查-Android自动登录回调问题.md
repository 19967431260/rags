---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 自动登录
platform: Android
title: Android自动登录回调问题
root_cause: 手动登录成功后未保存登录信息，导致自动登录无法获取信息
solution: 参考登录最佳实践：https://doc.yunxin.163.com/messaging/guide/DE1NjMxNjU?platform=android。确保手动登录成功后保存登录信息，自动登录才能正常回调。
customers:
  - 深圳岸涌
source: chat_history
tags:
  - Android
  - 自动登录
  - 回调
  - 登录信息
created: '2025-06-25'
updated: '2025-03-23'
---

## 问题：Android Android自动登录回调问题

## 问题详情

**现象**：
Android进app时既有手动登录又有自动登录，去掉手动登录后发现自动登录没有回调。

## 问题原因

手动登录成功后未保存登录信息，导致自动登录无法获取信息

## 解决方案

参考登录最佳实践：https://doc.yunxin.163.com/messaging/guide/DE1NjMxNjU?platform=android。确保手动登录成功后保存登录信息，自动登录才能正常回调。
