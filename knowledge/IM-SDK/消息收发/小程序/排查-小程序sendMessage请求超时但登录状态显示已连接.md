---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息收发
platform: 小程序
title: 小程序sendMessage请求超时但登录状态显示已连接
root_cause: 网络波动导致IM长链接短暂断开，但SDK内部状态刷新存在延迟，导致获取登录状态时返回已连接但实际发送失败
solution: 1. 增加onLoginStatus/onConnectStatus/onDisconnected/onConnectFailed事件回调监听连接状态变化
2. 升级SDK到10.8.0版本（10.7.1已修复部分重连场景）
customers: ['天津谷川']
source: chat_history
tags: ['sendMessage', '请求超时', '登录状态', '长链接', '微信小程序', 'SDK升级']
created: 2025-02-25
updated: 2026-03-23
---

## 问题：小程序 小程序sendMessage请求超时但登录状态显示已连接

## 问题详情

**现象**：
微信小程序端调用sendMessage发送消息时出现请求超时错误，但获取登录状态返回1（已连接）。服务端日志显示发送时间点(22:50:12)与心跳超时离线时间点(22:50:15)接近，存在网络波动导致IM长链接断开的可能。

**环境信息**：
- 平台：小程序
- 产品：IM-SDK

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客户提供错误截图和账号信息 → 技术支持查看服务端日志
2. 对比发送时间点和服务端离线时间点 → 发现时间接近，判断为网络波动导致长链接断开
3. 客户反馈获取登录状态为1但发送失败 → 建议增加onLoginStatus/onConnectStatus/onDisconnected/onConnectFailed事件回调监听
4. 建议复现时获取SDK console日志 → 同时建议升级SDK到10.8.0版本（当前10.6.0，10.7.1有重连场景修复）

## 问题原因

网络波动导致IM长链接短暂断开，但SDK内部状态刷新存在延迟，导致获取登录状态时返回已连接但实际发送失败

## 解决方案

1. 增加onLoginStatus/onConnectStatus/onDisconnected/onConnectFailed事件回调监听连接状态变化
2. 升级SDK到10.8.0版本（10.7.1已修复部分重连场景）

## 其他触发场景

（合并时在此处追加：`- [小程序] 小程序sendMessage请求超时但登录状态显示已连接，来源：['天津谷川']，2026-03-23`）
