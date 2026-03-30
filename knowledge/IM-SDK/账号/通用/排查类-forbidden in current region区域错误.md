---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 账号
platform: 通用
title: forbidden in current region区域错误
root_cause: 应用是国内应用，但请求使用了海外域名(-sg后缀)
solution: 国内应用需要将api-sg.netease.im改为api.netease.im，去掉-sg后缀。
customers: ['厦门二零六']
source: chat_history
tags: ['forbidden', 'region', '区域', '国内', '域名']
created: 2025-01-02
updated: 2026-03-23
---

## 问题：forbidden in current region区域错误

## 问题详情

**现象**：
客户注册时返回forbidden in current region错误。

## 排查过程



## 问题原因

应用是国内应用，但请求使用了海外域名(-sg后缀)

## 解决方案

国内应用需要将api-sg.netease.im改为api.netease.im，去掉-sg后缀。

## 其他触发场景

（合并时在此处追加）
