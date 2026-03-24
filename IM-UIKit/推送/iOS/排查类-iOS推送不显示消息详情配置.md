---
track_type: 排查类
sub_type: 使用问题
product: IM-UIKit
feature: 推送
platform: iOS
title: iOS推送不显示消息详情配置
root_cause: 需要在接收端而非发送端配置推送设置，且需在登录成功后调用
solution: 接收端登录成功后调用：let setting = NIMPushNotificationSetting(); setting.type = .noDetail; NIMSDK.shared().apnsManager.updateApnsSetting(setting)
customers: ['同城在线']
source: chat_history
tags: ['推送', 'APNs', 'noDetail', 'iOS', 'UIKit', '消息详情']
created: 2025-01-03
updated: 2026-03-23
---

## 问题：iOS推送不显示消息详情配置

## 问题详情

**现象**：
客户希望推送内容不显示消息具体信息，只显示'xxx给你发送了一条消息'。在UIKit中配置willSendMessage修改apnsContent和apnsPayload后仍显示详情。

## 排查过程

1. 客户尝试在willSendMessage中修改apnsContent和apnsPayload
2. 发现UIKit封装的willsend方法需要调用super
3. 检查后台推送设置，已开启不显示详情开关
4. 发现推送token未上报，指导客户上传deviceToken
5. 建议客户使用SDK底层方法NIMPushNotificationSetting设置type为noDetail
6. 确认需要在接收端登录成功后调用updateApnsSetting

## 问题原因

需要在接收端而非发送端配置推送设置，且需在登录成功后调用

## 解决方案

接收端登录成功后调用：let setting = NIMPushNotificationSetting(); setting.type = .noDetail; NIMSDK.shared().apnsManager.updateApnsSetting(setting)

## 其他触发场景

（合并时在此处追加）
