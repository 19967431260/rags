---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 通知栏推送
platform: Android
title: Android通知栏多消息合并后点击无法跳转
root_cause: 服务器API下发消息时未正确配置推送参数，导致通知栏消息无法正常触发跳转
solution: 服务器API请求下发的消息默认就能触发通知栏，前提是：1. app本身在后台；2. setChattingAccount两个参数均为NONE。
customers:
  - 深圳对娱信息技术有限公司
source: chat_history
tags:
  - 通知栏
  - 推送
  - 消息合并
  - 点击跳转
  - 小米手机
  - Android
created: '2025-06-22'
updated: '2025-03-23'
---

## 问题：Android Android通知栏多消息合并后点击无法跳转

## 问题详情

**现象**：
小米手机下，通知栏显示多条消息合并后，点击通知无法跳转到应用。单条消息点击正常，多条消息合并后点击无反应。使用SDK版本9.14.2。

**排查过程**：

1. 确认单条消息点击正常，多条合并后无法点击
2. 排查通知ID和请求码是否重复
3. 测试demo确认按照会话折叠模式配置正常
4. 排查入口Activity设置问题
5. 最终确认是服务器API下发消息的配置问题

**关键发现**：服务器API下发消息时未正确配置推送参数，导致通知栏消息无法正常触发跳转

## 问题原因

服务器API下发消息时未正确配置推送参数，导致通知栏消息无法正常触发跳转

## 解决方案

服务器API请求下发的消息默认就能触发通知栏，前提是：1. app本身在后台；2. setChattingAccount两个参数均为NONE。
