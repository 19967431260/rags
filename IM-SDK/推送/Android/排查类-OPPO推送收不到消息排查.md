---
track_type: 排查类
sub_type: 测试问题
product: IM-SDK
feature: 推送
platform: Android
title: OPPO推送收不到消息排查
root_cause: OPPO推送服务端返回成功，问题可能出在客户端权限或OPPO推送通道
solution: OPPO推送服务端返回成功但收不到消息时：1. 检查应用推送权限是否开启；2. 如权限已开启，将messageid提供给OPPO推送技术支持进一步排查。
customers: ['深圳宸瑞麟科技技术对接群']
source: chat_history
tags: ['IM-SDK', 'OPPO推送', '离线推送', 'messageId']
created: 2025-01-16
updated: 2026-03-23
---

## 问题：OPPO推送收不到消息排查

## 问题详情

**现象**：
客户反馈OPPO推送收不到消息，提供push token后需要排查原因。

## 排查过程

1. 客户提供OPPO push token
2. 技术支持查询发现OPPO返回成功：result = {code=0, data={messageId=...}, message=Success}
3. 建议检查应用推送权限是否开启
4. 如权限已开启，建议将messageid提供给OPPO技术支持查询

## 问题原因

OPPO推送服务端返回成功，问题可能出在客户端权限或OPPO推送通道

## 解决方案

OPPO推送服务端返回成功但收不到消息时：1. 检查应用推送权限是否开启；2. 如权限已开启，将messageid提供给OPPO推送技术支持进一步排查。

## 其他触发场景

（合并时在此处追加）
