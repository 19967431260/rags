---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 登录服务
platform: Android
title: 更换包名后IM登录失败
root_cause: 控制台开启包名验证，新包名未添加
solution: 在控制台添加新包名com.jimei.chuangyetianxia，或关闭包名验证
customers: ["创业天下"]
source: chat_history
tags: ["登录失败", "包名", "包名验证", "授权"]
created: 2025-11-07
updated: 2026-03-20
---

## 问题：Android 更换包名后IM登录失败

## 问题详情

**现象**：
客户更换包名后IM登录失败，咨询是否需要重新申请授权。

## 排查过程

1. 确认包名验证设置
2. 检查控制台配置
**关键发现**：控制台开启了包名验证

## 问题原因

控制台开启包名验证，新包名未添加

## 解决方案

在控制台添加新包名com.jimei.chuangyetianxia，或关闭包名验证

## 其他触发场景

