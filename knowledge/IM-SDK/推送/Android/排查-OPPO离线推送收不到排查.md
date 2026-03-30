---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 推送
platform: Android
title: OPPO离线推送收不到排查
root_cause: OPPO通知通道需要客户端自行创建
solution: OPPO的通知通道需要客户端自己创建，检查通知权限是否全部开启
customers: ["VIP云信-武汉梦匠科技有限公司"]
source: chat_history
tags: ["OPPO", "推送", "离线", "通知通道", "Android"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：OPPO离线推送收不到排查

## 问题详情

**现象**：
Android端OPPO推送配置完成后，离线通知收不到

**环境信息**：
- 平台：Android

## 排查过程

1. 客户反馈OPPO离线推送收不到
2. 查看日志发现OPPO返回成功
3. 建议检查通知权限设置
4. 提示需要客户端创建通知通道

## 根因分析

OPPO通知通道需要客户端自行创建

## 解决方案

OPPO的通知通道需要客户端自己创建，检查通知权限是否全部开启

## 其他触发场景

（无）
