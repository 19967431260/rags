---
track_type: 排查类
sub_type: 功能异常
product: RTC
feature: 直播
platform: Server
title: 直播服务端API返回'频道信息与当前用户不匹配'错误
root_cause: 对应cid被删除或cid和appkey不匹配
solution: 检查cid是否被删除，确认cid和appkey的匹配关系
customers: ["FVIP-云信-江苏盖睿健康"]
source: chat_history
tags: ["音视频2.0", "直播", "API错误", "频道信息不匹配", "cid"]
created: 2025-12-08
updated: 2026-03-23
---

## 问题：直播服务端API返回'频道信息与当前用户不匹配'错误

## 问题详情

**现象**：
调用直播服务端API时返回"频道信息与当前用户不匹配"错误。

**环境信息**：
- 产品：音视频2.0
- 平台：Server

## 排查过程

1. 检查cid状态 → 发现cid可能被删除
2. 检查cid和appkey匹配关系 → 发现可能不匹配

**关键发现**：对应cid被删除或cid和appkey不匹配导致错误

## 问题原因

对应cid被删除了，或者cid和appkey不匹配。

## 解决方案

检查cid是否被删除，确认cid和appkey的匹配关系。

参考文档：https://faq.yunxin.163.com/#KB0169

## 其他触发场景

