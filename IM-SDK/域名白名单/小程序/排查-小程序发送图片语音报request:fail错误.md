---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 域名白名单
platform: 小程序
title: 小程序发送图片语音报request:fail错误
root_cause: 小程序白名单未配置NOS等必要域名。
solution: 需要在小程序后台配置NOS域名及其他相关域名到白名单，具体域名列表参考文档：https://doc.yunxin.163.com/messaging/guide?platform=uniapp
customers: ['上海怡明机动车驾驶员培训有限公司']
source: chat_history
tags: ['小程序', '白名单', 'NOS', '图片', '语音', 'request:fail']
created: 2025-01-14
updated: 2026-03-23
---

## 问题：小程序 小程序发送图片语音报request:fail错误

## 问题详情

**现象**：
客户反馈真机发送图片和语音报request:fail错误，文字正常。

## 排查过程

1. 怀疑NOS地址未加到小程序白名单
2. 提供文档中的域名配置列表

## 问题原因

小程序白名单未配置NOS等必要域名。

## 解决方案

需要在小程序后台配置NOS域名及其他相关域名到白名单，具体域名列表参考文档：https://doc.yunxin.163.com/messaging/guide?platform=uniapp

## 其他触发场景

（合并时在此处追加）
