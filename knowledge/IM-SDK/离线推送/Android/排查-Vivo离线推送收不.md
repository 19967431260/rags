---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 离线推送
platform: Android
title: Vivo离线推送收不到
root_cause: 发送的是自定义系统通知，且未设置push_config中的push_content和push_enabled参数
solution: 系统通知需要设置push_config，push_content一定要设置值，push_enabled设为true
customers: ["点点云智能科技有限公司"]
source: chat_history
tags: ["离线推送", "vivo", "系统通知", "push_config", "push_content"]
created: 2025-02-26
updated: 2026-03-20
---

## 问题：Android Vivo离线推送收不到

## 问题详情

**现象**：
调用接口后收不到离线推送，使用vivo手机。

## 排查过程

1. 查询接收方云信账号 → 有推送token
2. 询问app进程是否杀死 → 已杀死
3. 询问发送方账号 → 客户提供的是token
4. 确认appkey → 正确
5. 发现是自己发给自己 → 不会触发推送
6. 换账号测试 → 还是收不到
7. 发现发送的是自定义系统通知不是消息
8. 检查push_config设置 → 未设置推送参数

## 问题原因

发送的是自定义系统通知，且未设置push_config中的push_content和push_enabled参数

## 解决方案

系统通知需要设置push_config，push_content一定要设置值，push_enabled设为true

## 其他触发场景
- [Android] Vivo离线推送收不到，来源：['点点云智能科技有限公司']，2026-03-20

