---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 网络连接
platform: Web
title: Web端socket连接失败LBS请求被拦截
root_cause: 网络环境拦截了LBS请求，无法获取IM服务器link地址
solution: 检查并放行白名单域名：https://lbs-sdk.netease.im 和 https://lbs.netease.im
customers: ['vivo-v消息']
source: chat_history
tags: ['Web', 'socket', 'LBS', '连接失败', '白名单', '网络拦截']
created: 2025-01-08
updated: 2026-03-23
---

## 问题：Web Web端socket连接失败LBS请求被拦截

## 问题详情

**现象**：
Web端用户无法连接socket，一直在重试。访问lbs.netease.im提示Internet访问被阻止。

## 排查过程

1. 用户访问LBS地址被拦截
2. 确认网络设备阻止了LBS请求
3. 需要检查白名单域名
**关键发现**：LBS请求被网络拦截导致无法获取link地址

## 问题原因

网络环境拦截了LBS请求，无法获取IM服务器link地址

## 解决方案

检查并放行白名单域名：https://lbs-sdk.netease.im 和 https://lbs.netease.im

## 其他触发场景

（合并时在此处追加）
