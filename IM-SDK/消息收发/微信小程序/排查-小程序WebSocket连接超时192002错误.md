---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息收发
platform: 微信小程序
title: 小程序WebSocket连接超时192002错误
root_cause:
solution: 1. 在小程序管理后台的服务器域名白名单中添加wlnimsc0.netease.im:443（带端口号）；2. 如仍有部分用户无法连接，需排查用户本地网络环境限制
customers: ["杭州米加健康科技有限公司"]
source: chat_history
tags: ["小程序", "WebSocket", "192002", "connect timeout", "白名单"]
created: 2026-02-12
updated: 2026-03-17
---

## 问题：微信小程序 小程序WebSocket连接超时192002错误

## 问题详情

**现象**：
小程序连接wlnimsc0.netease.im:443时报错connect timeout（错误码192002），部分用户可以连接，部分用户无法连接。

## 排查过程

1. 检查小程序服务器域名白名单配置 → 已配置但未带端口
2. 建议添加端口号到白名单 → 仍然失败
3. 检查网络环境 → 部分用户可连接部分不可，排除VPN和本地网络限制

**关键发现**：问题与用户网络环境相关，非SDK或配置问题

## 问题原因



## 解决方案

1. 在小程序管理后台的服务器域名白名单中添加wlnimsc0.netease.im:443（带端口号）
2. 如仍有部分用户无法连接，需排查用户本地网络环境限制

## 其他触发场景
