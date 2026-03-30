---
track_type: 排查类
sub_type: 使用问题
product: IM V10
feature: 离线推送
platform: 鸿蒙
title: 鸿蒙-Android系统离线推送收不到
root_cause: 华为平台针对非营销类消息会限制推送频率，发送消息时未配置category字段导致被限频
solution: 发送消息时需要在payload下的hwfield的androidconfig中配置category字段。华为、小米等厂商都有类似的分类字段要求（如小米的channel_id）。参考文档：https://doc.yunxin.163.com/messaging/guide/jg2ODQxMjU?platform=android#%E5%8D%8E%E4%B8%BA%E5%B9%B3%E5%8F%B0%E9%99%90%E5%88%B6
customers: ["招银国际"]
source: chat_history
tags: ["鸿蒙", "华为推送", "离线推送", "category", "限频"]
created: 2026-01-07
updated: 2026-03-15
---

## 问题：鸿蒙 鸿蒙-Android系统离线推送收不到

## 问题详情

**现象**：
客户在测试环境调试华为鸿蒙-Android系统（鸿蒙3.0），离线推送手机一直收不到。在华为平台手动推送可以收到，但通过云信推送收不到。早上测试正常，下午开始收不到。

## 排查过程

1. 检查客户端日志 → token上报正常，前置流程没问题 2. 检查推送证书配置 → 已配置 3. 确认消息分类category是否配置 → 未配置

## 问题原因

华为平台针对非营销类消息会限制推送频率，发送消息时未配置category字段导致被限频

## 解决方案

发送消息时需要在payload下的hwfield的androidconfig中配置category字段。华为、小米等厂商都有类似的分类字段要求（如小米的channel_id）。参考文档：https://doc.yunxin.163.com/messaging/guide/jg2ODQxMjU?platform=android#%E5%8D%8E%E4%B8%BA%E5%B9%B3%E5%8F%B0%E9%99%90%E5%88%B6

## 其他触发场景

（合并时在此处追加）
