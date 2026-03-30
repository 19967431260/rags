---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 离线推送
platform: Android
title: OPPO离线推送未收到消息
root_cause: 云信侧推送请求成功，问题在OPPO厂商通道侧
solution: 云信侧返回messageId为32390287-1-1-67bd2e0d04fad901825307b4，需联系OPPO侧根据messageId查询推送状态
customers: ["VIP云信-广州市点图网络科技有限公司"]
source: chat_history
tags: ["离线推送", "OPPO", "厂商推送", "未收到推送"]
created: 2025-02-25
updated: 2026-03-20
---

## 问题：Android OPPO离线推送未收到消息

## 问题详情

**现象**：
OPPO手机用户未收到离线推送消息，token为OPPO_CN_94a265593956dd28149fa8113f0bf5bc。

## 排查过程

1. 检查云信侧推送请求记录 → 显示call_success请求成功
2. 确认channel_id配置正确
3. 客户端通知设置已开启
4. 建议联系OPPO侧根据messageId排查

## 问题原因

云信侧推送请求成功，问题在OPPO厂商通道侧

## 解决方案

云信侧返回messageId为32390287-1-1-67bd2e0d04fad901825307b4，需联系OPPO侧根据messageId查询推送状态

## 其他触发场景

