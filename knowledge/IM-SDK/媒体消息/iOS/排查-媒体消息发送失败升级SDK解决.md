---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 媒体消息
platform: iOS
title: 媒体消息发送失败升级SDK解决
root_cause: 
solution: 详见正文。
customers: ["智慧丘比特"]
source: chat_history
tags: ["媒体消息", "发送失败", "SDK升级", "域名解析", "iOS"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题描述

用户反馈发送媒体消息（语音、图片）发送不出去，文字消息能正常发送，登录状态正常。

## 排查过程

1. 客户反馈媒体消息发送失败 → 询问用户反馈时间点和accid
2. 拉不到用户日志 → 怀疑上传域名解析失败
3. 建议升级SDK到最新版本9.19.10 → 新版本支持下发IP地址用于文件上传
4. 客户误升级V10 → 提醒老项目使用V9版本

## 根因分析

怀疑上传域名解析失败，老版本SDK不支持IP地址下发

## 解决方案

升级SDK到V9最新版本9.19.10，新版本支持下发IP地址用于文件上传验证域名解析问题
