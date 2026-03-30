---
track_type: 排查类
sub_type: 测试问题
product: IM-SDK
feature: 推送
platform: Android
title: 小米离线推送收不到消息-channel id配置问题
root_cause: 小米推送channel id配置不正确导致推送失败
solution: 小米推送需要正确配置channel id。出现ErrorCode=27001: invalid channel info!错误时，需要检查控制台和代码中的channel id配置是否一致，并联系小米推送技术支持确认channel配置是否正确。
customers: ['深圳宸瑞麟科技技术对接群']
source: chat_history
tags: ['IM-SDK', '小米推送', '离线推送', 'channel id', '27001']
created: 2025-01-10
updated: 2026-03-23
---

## 问题：小米离线推送收不到消息-channel id配置问题

## 问题详情

**现象**：
客户反馈小米离线推送收不到消息，push注册成功但消息无法送达。

## 排查过程

1. 客户反馈小米推送注册成功但收不到消息
2. 查看日志发现failReason = ErrorCode=27001: invalid channel info!
3. 技术支持指出小米推送的channel id配置有问题
4. 建议客户联系小米技术支持确认channel id配置

## 问题原因

小米推送channel id配置不正确导致推送失败

## 解决方案

小米推送需要正确配置channel id。出现ErrorCode=27001: invalid channel info!错误时，需要检查控制台和代码中的channel id配置是否一致，并联系小米推送技术支持确认channel配置是否正确。

## 其他触发场景

（合并时在此处追加）
