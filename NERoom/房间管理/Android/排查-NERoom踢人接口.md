---
track_type: 排查类
sub_type: 使用问题
product: NERoom
feature: 房间管理
platform: Android
title: NERoom踢人接口kickMemberOut调用问题
root_cause: 控制台配置未保存
solution: 在控制台配置踢人权限后需要点击保存，配置才能生效
customers: ["高途预见塔塔项目"]
source: chat_history
tags: ["NERoom", "Android", "kickMemberOut", "房间管理"]
created: 2025-02-11
updated: 2026-03-20
---

## 问题：Android NERoom踢人接口kickMemberOut调用问题

## 问题详情

**现象**：
调用kickMemberOut方法踢人时出现问题，需要确认配置。

## 排查过程

1. 客户反馈调用kickMemberOut方法异常
2. 确认对应的key配置
3. 发现客户未保存配置导致问题
4. 重新保存后解决

## 问题原因

控制台配置未保存

## 解决方案

在控制台配置踢人权限后需要点击保存，配置才能生效

## 其他触发场景
- [Android] NERoom踢人接口kickMemberOut调用问题，来源：['高途预见塔塔项目']，2026-03-20
- [Android] NERoom踢人接口kickMemberOut调用问题，来源：['高途预见塔塔项目']，2026-03-20

