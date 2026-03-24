---
track_type: 排查类
sub_type: 集成类
product: 呼叫组件
feature: 权限配置
platform: iOS
title: 1v1 demo视频通话报无权限错误
root_cause: 控制台未开启信令功能
solution: 在云信控制台IM功能设置中勾选开启信令功能。
customers: ['AB Leisure Exponent Inc']
source: chat_history
tags: ['呼叫组件', '1v1', '权限', '信令', '控制台']
created: 2025-01-23
updated: 2026-03-23
---

## 问题：iOS 1v1 demo视频通话报无权限错误

## 问题详情

**现象**：
点击视频通话按钮时控制台报错，提示没有权限。

## 排查过程

1. 客户反馈视频通话报错 → 技术支持查看报错信息 → 确认是没有权限 → 询问appkey → 客户提供appkey → 技术支持查询后台 → 发现未开启信令功能

## 问题原因

控制台未开启信令功能

## 解决方案

在云信控制台IM功能设置中勾选开启信令功能。

## 其他触发场景

（合并时在此处追加）
