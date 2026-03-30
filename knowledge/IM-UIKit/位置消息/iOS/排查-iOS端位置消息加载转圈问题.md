---
track_type: 排查类
sub_type: 集成类
product: IM-UIKit
feature: 位置消息
platform: iOS
title: iOS端位置消息加载转圈问题
root_cause: 高德API Key未正确配置，缺少安全密钥(serverKey)
solution: 参考文档https://doc.yunxin.163.com/messaging-uikit/guide/TAyMDY4NjY?platform=iOS配置高德API Key，serverKey对应高德侧的安全密钥。
customers: ['宁德市腾时网络科技']
source: chat_history
tags: ['UIKit', '位置消息', '高德地图', 'iOS', '转圈']
created: 2025-01-08
updated: 2026-03-23
---

## 问题：iOS iOS端位置消息加载转圈问题

## 问题详情

**现象**：
iOS端IM-UIKit位置消息加载时一直显示转圈，无法正常显示位置信息。

## 排查过程

1. 客户反馈消息能加载但持续转圈 → 2. 排查发现与高德地图API Key配置相关 → 3. 确认需要配置高德serverKey（安全密钥）

## 问题原因

高德API Key未正确配置，缺少安全密钥(serverKey)

## 解决方案

参考文档https://doc.yunxin.163.com/messaging-uikit/guide/TAyMDY4NjY?platform=iOS配置高德API Key，serverKey对应高德侧的安全密钥。

## 其他触发场景

（合并时在此处追加）
