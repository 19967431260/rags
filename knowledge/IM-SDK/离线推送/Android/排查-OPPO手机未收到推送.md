---
track_type: 排查类
sub_type: 配置开通咨询
product: IM-SDK
feature: 离线推送
platform: Android
title: OPPO手机未收到推送
root_cause: 云信管理后台配置的OPPO推送证书appsecret与OPPO推送管理后台的mastersecret不一致
solution: 检查云信管理后台配置的推送证书和OPPO后台的mastersecret配置信息是否一致
customers: ['北京爱豆文化传媒有限公司']
source: chat_history
tags: ['OPPO推送', '推送失败', 'appsecret', 'mastersecret']
created: 2025-02-11
updated: 2026-03-23
---

## 问题：Android OPPO手机未收到推送

## 问题详情

**现象**：
OPPO手机未收到相关推送，需要检查后台日志。

**环境信息**：
- 平台：Android
- 产品：IM-SDK

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 检查后台推送记录 → 发现token未上报
2. 检查证书配置 → 发现云信后台配置的appsecret与OPPO后台的mastersecret不一致
3. 关键发现：云信管理后台上传的推送证书appsecret配置错误

## 问题原因

云信管理后台配置的OPPO推送证书appsecret与OPPO推送管理后台的mastersecret不一致

## 解决方案

检查云信管理后台配置的推送证书和OPPO后台的mastersecret配置信息是否一致

## 其他触发场景

（合并时在此处追加：`- [Android] OPPO手机未收到推送，来源：['北京爱豆文化传媒有限公司']，2026-03-23`）
