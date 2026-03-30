---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 自定义通知
platform: Flutter
title: Flutter sendCustomNotification返回-1错误
root_cause: NIMSendCustomNotificationParams中的参数未正确初始化，部分配置对象需要创建实例
solution: 需要正确初始化NIMSendCustomNotificationParams中的各个配置对象：antispamConfig、notificationConfig、pushConfig、routeConfig都需要创建对应实例，不能为null。
customers: ['广西源龙网络科技有限公司']
source: chat_history
tags: ['sendCustomNotification', '-1', 'Flutter', 'nim_core_v2', '参数初始化']
created: 2025-01-22
updated: 2026-03-23
---

## 问题：Flutter Flutter sendCustomNotification返回-1错误

## 问题详情

**现象**：
在Flutter平台使用sendCustomNotification发送自定义通知时，接口返回-1错误。客户使用的是nim_core_v2: ^10.4.0版本。

## 排查过程

1. 客户反馈sendCustomNotification返回-1错误
2. 技术支持建议检查参数是否有必传字段设置为null
3. 客户确认参数没有null值
4. 技术支持要求打印sessionId和receiverId参数
5. 客户提供了参数截图
6. 技术支持建议先不传params参数，只传前两个参数测试
7. 客户测试后仍有问题
8. 最终技术支持提供了正确的参数初始化示例代码

## 问题原因

NIMSendCustomNotificationParams中的参数未正确初始化，部分配置对象需要创建实例

## 解决方案

需要正确初始化NIMSendCustomNotificationParams中的各个配置对象：antispamConfig、notificationConfig、pushConfig、routeConfig都需要创建对应实例，不能为null。

## 其他触发场景

（合并时在此处追加）
