---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 离线推送
platform: iOS
title: iOS离线推送证书失效导致推送失败
root_cause: iOS推送证书被苹果吊销，导致APNS连接建立失败，无法发送离线推送
solution: 重新生成iOS推送证书(p12格式)，在云信控制台编辑推送配置，删除旧证书并上传新证书
customers:
  - 湖南敏肤
source: chat_history
tags:
  - IM
  - iOS
  - 离线推送
  - APNS
  - 证书失效
  - certificate_revoked
created: '2025-06-03'
updated: '2025-03-23'
---

## 问题：iOS iOS离线推送证书失效导致推送失败

## 问题详情

**现象**：
客户反馈群内成员部分能收到离线推送，部分收不到。排查发现APNS推送证书被吊销(certificate_revoked)，导致推送连接建立失败。

**排查过程**：

1. 客户反馈群内A能收到推送，B收不到
2. 查询推送日志 → 发现APNS_HTTP2_PUSH_FAIL错误
3. 关键错误：SSLHandshakeException: Received fatal alert: certificate_revoked
4. 判断推送证书mf_ios已被吊销失效

**关键发现**：iOS推送证书被苹果吊销，导致APNS连接建立失败，无法发送离线推送

## 问题原因

iOS推送证书被苹果吊销，导致APNS连接建立失败，无法发送离线推送

## 解决方案

重新生成iOS推送证书(p12格式)，在云信控制台编辑推送配置，删除旧证书并上传新证书
