---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 离线推送
platform: iOS
title: iOS APNs推送收不到排查
root_cause: 客户做了登录状态判断，拦截了DeviceToken上报给云信服务端。
solution: 需要在登录成功后调用云信接口将APNs DeviceToken上报给服务端，参考文档：https://doc.yunxin.163.com/messaging/guide/DMxMjU0MDY?platform=iOS
customers: ['上海导毕教育科技有限公司长沙分公司']
source: chat_history
tags: ['iOS', 'APNs', '推送', 'DeviceToken', '离线推送']
created: 2025-01-21
updated: 2026-03-23
---

## 问题：iOS iOS APNs推送收不到排查

## 问题详情

**现象**：
客户反馈debug测试APNs推送收到了，但打包后自己的业务推送收不到。

## 排查过程

1. 检查日志发现客户未调用云信接口将DeviceToken传给服务端
2. 客户确认做了登录状态判断拦截了token上报
3. 建议重新调用token上报接口再测试

## 问题原因

客户做了登录状态判断，拦截了DeviceToken上报给云信服务端。

## 解决方案

需要在登录成功后调用云信接口将APNs DeviceToken上报给服务端，参考文档：https://doc.yunxin.163.com/messaging/guide/DMxMjU0MDY?platform=iOS

## 其他触发场景

（合并时在此处追加）
