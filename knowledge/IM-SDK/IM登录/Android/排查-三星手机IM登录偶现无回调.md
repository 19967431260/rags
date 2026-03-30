---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: IM登录
platform: Android
title: 三星手机IM登录偶现无回调
root_cause: 手动登录成功后未正确保存登录信息，导致自动登录时信息为空
solution: 参考登录最佳实践调整：https://doc.yunxin.163.com/messaging/guide/DE1NjMxNjU?platform=android。确保手动登录成功后保存登录信息。
customers:
  - 深圳岸涌
source: chat_history
tags:
  - Android
  - IM登录
  - 无回调
  - 三星
  - 自动登录
created: '2025-06-24'
updated: '2025-03-23'
---

## 问题：Android 三星手机IM登录偶现无回调

## 问题详情

**现象**：
三星手机调用IM登录偶现没有回调，会话列表页面判断没有在线。

**排查过程**：

1. 查看SDK日志发现切回前台走自动登录时信息为空
2. 怀疑是手动登录成功后没保存登录信息
3. 建议参考登录最佳实践调整

**关键发现**：手动登录成功后未正确保存登录信息，导致自动登录时信息为空

## 问题原因

手动登录成功后未正确保存登录信息，导致自动登录时信息为空

## 解决方案

参考登录最佳实践调整：https://doc.yunxin.163.com/messaging/guide/DE1NjMxNjU?platform=android。确保手动登录成功后保存登录信息。
