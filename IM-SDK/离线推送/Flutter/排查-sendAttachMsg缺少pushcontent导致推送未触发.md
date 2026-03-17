---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 离线推送
platform: Flutter
title: 自定义系统通知离线推送未收到
root_cause: 服务端调用sendAttachMsg接口发送自定义系统通知时，未传递pushcontent参数，导致离线推送未触发
solution: 调用sendAttachMsg接口时必须传递pushcontent参数（推送文案，最长500字符），attach参数必传，option参数可选。参考：pushcontent="云信测试，点此查看"，attach需包含消息类型和内容
customers: ["武汉市德上云科技有限公司"]
source: chat_history
tags: ["sendAttachMsg", "pushcontent", "自定义系统通知", "离线推送", "Flutter"]
created: 2026-02-03
updated: 2026-03-17
---

## 问题：Flutter 自定义系统通知离线推送未收到

## 问题详情

**现象**：
Flutter端通过服务端API发送自定义系统通知（sendAttachMsg），离线时未收到推送。客户端已上报推送token，使用knuff工具测试证书和token正常，但服务端调用接口发送时无推送记录。应用内监听onCustomNotification可以收到消息，但离线推送收不到。

**环境信息**：
- 平台：Flutter

## 排查过程

1. 检查服务端API调用参数 → 发现未传pushcontent参数
2. 检查推送token上报 → 确认token已上报
3. 后台查询推送记录 → 无推送记录，代表未触发推送
4. 技术支持使用测试环境复现 → 传入pushcontent和attach参数后推送成功

**关键发现**：服务端调用sendAttachMsg接口时缺少pushcontent参数，导致离线推送未触发

## 问题原因

服务端调用sendAttachMsg接口发送自定义系统通知时，未传递pushcontent参数，导致离线推送未触发

## 解决方案

调用sendAttachMsg接口时必须传递pushcontent参数（推送文案，最长500字符），attach参数必传，option参数可选。参考：pushcontent="云信测试，点此查看"，attach需包含消息类型和内容

## 其他触发场景
