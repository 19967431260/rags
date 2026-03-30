---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 登录
platform: Android
title: Android SDK NimUIKit.login返回415错误码
root_cause: 客户端和服务器建立连接失败，可能由VPN、DNS缓存、防火墙或SDK版本导致
solution: 检查VPN/网络环境，升级SDK到最新版本支持IPv6，排查防火墙拦截
customers: ["南京蓝鲸人-美篇"]
source: chat_history
tags: ["415","login","连接失败","VPN","IPv6"]
created: 2025-02-27
updated: 2025-03-20
---

## 问题：Android Android SDK NimUIKit.login返回415错误码

## 问题详情

**现象**：
用户反馈Android端调用NimUIKit.login登录时返回错误码415，无法建立连接。

## 排查过程

1. 确认用户是否开启VPN → 需切换网络测试
2. 检查DNS缓存 → 可能获取到已下线服务器IP
3. 防火墙检查 → 建议更换4G或热点对比
4. SDK版本检查 → 旧版SDK不支持IPv6需升级

**关键发现**：客户端和服务器建立连接失败

## 问题原因

客户端和服务器建立连接失败，可能由VPN、DNS缓存、防火墙或SDK版本导致。

## 解决方案

检查VPN/网络环境，升级SDK到最新版本支持IPv6，排查防火墙拦截。

## 其他触发场景

