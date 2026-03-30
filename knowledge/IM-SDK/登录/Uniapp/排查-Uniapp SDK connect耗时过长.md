---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 登录
platform: Uniapp
title: Uniapp SDK connect耗时过长
root_cause: SDK版本过低（0.15.1）存在连接兼容性问题
solution: 升级nim-web-sdk-ng到0.19.2或更高版本
customers: ['VIP云信-浙江橙遇科技有限公司']
source: chat_history
tags: ['登录', 'connect', 'uniapp', 'SDK升级', '连接超时']
created: 2025-01-16
updated: 2026-03-23
---

## 问题：Uniapp Uniapp SDK connect耗时过长

## 问题详情

**现象**：
客户使用uniapp调用nim.connect()登录时，卡在init3步骤，connect耗时很长无法登录。

## 排查过程

1. 客户反馈connect卡在init3
2. 查看日志发现lbs请求成功，但link连接卡住
3. 尝试切换WiFi和流量均无效
4. 客服建议升级SDK版本
**关键发现**：SDK版本0.15.1存在连接问题，升级后解决

## 问题原因

SDK版本过低（0.15.1）存在连接兼容性问题

## 解决方案

升级nim-web-sdk-ng到0.19.2或更高版本

## 其他触发场景

（合并时在此处追加）
