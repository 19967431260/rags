---
track_type: 排查类
sub_type: 配置问题
product: IM V9
feature: 消息推送
platform: iOS
title: iOS推送证书更新后推送失败
root_cause: 推送证书更新后未正确配置或证书环境不匹配
solution: 重新上传正确的推送证书到云信控制台，确保证书环境与APP环境一致。
customers: ["晋商银行"]
source: chat_history
tags: ["iOS", "推送", "证书", "配置", "APNs"]
created: 2026-01-13
updated: 2026-03-15
---

## 问题：iOS iOS推送证书更新后推送失败

## 问题详情

**现象**：
客户更新了iOS推送证书，但推送仍然失败。appkey: 4e1e1d8c0e8c3c5b8e8e8e8e8e8e8e8e（示例），需要排查推送配置问题。

## 排查过程

1. 检查新证书是否正确上传到云信控制台 2. 确认证书环境（开发/生产）是否匹配 3. 验证deviceToken是否有效

## 问题原因

推送证书更新后未正确配置或证书环境不匹配

## 解决方案

重新上传正确的推送证书到云信控制台，确保证书环境与APP环境一致。

## 其他触发场景

（合并时在此处追加）
