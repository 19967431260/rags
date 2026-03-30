---
track_type: 排查类
sub_type: 线上事故
product: IM-SDK
feature: 聊天室
platform: Android
title: Android端配置IPv6后聊天室登录返回415错误
root_cause: 由于运维必要操作，对客户配置的IPv6域名产生了影响，导致配置了IPv6的用户出现登录失败的情况。
solution: 短期方案：切换到IPv4网络或注释IPv6配置。长期方案：升级SDK到9.21.10版本，并在聊天室配置中增加兜底地址：option.serverConfig.chatRoomLinkList = new ArrayList<>(Arrays.asList("chatlink-cn.yunxinfw.com:443"))，当其他地址连不上时会走默认地址。
customers: ["可思达地信息科技"]
source: chat_history
tags: ["415", "IPv6", "聊天室登录", "网络异常", "Android"]
created: 2026-02-02
updated: 2026-03-17
---

## 问题：Android Android端配置IPv6后聊天室登录返回415错误

## 问题详情

**现象**：
客户反馈Android端聊天室登录失败，返回错误码415（客户端网络异常）。多个用户同时反馈无法登录聊天室，测试设备在WiFi和5G网络下均无法连接。必现。

**环境信息**：
- SDK 版本：9.14.2
- 系统版本 / 设备：Android平台
- 其他：已配置IPv6优先策略，iOS端未配置IPv6运行正常，约一半Android用户受影响

## 排查过程

1. 检查网络环境 → 确认未开启VPN/代理，WiFi和5G网络均无法连接
2. 检查SDK版本 → Android使用9.14.2，iOS使用9.20.18
3. 分析日志 → 发现客户端使用IPv6地址连接
4. 测试IPv4连接 → 将初始化配置中的IPv6设置注释后恢复正常
5. 服务端排查 → 确认是运维操作影响了IPv6域名解析

**关键发现**：客户配置了IPv6优先策略，服务端IPv6域名因运维操作受影响导致连接失败，切换到IPv4后恢复正常。

## 问题原因

由于运维必要操作，对客户配置的IPv6域名产生了影响，导致配置了IPv6的用户出现登录失败的情况。

## 解决方案

短期方案：切换到IPv4网络或注释IPv6配置。长期方案：升级SDK到9.21.10版本，并在聊天室配置中增加兜底地址：option.serverConfig.chatRoomLinkList = new ArrayList<>(Arrays.asList("chatlink-cn.yunxinfw.com:443"))，当其他地址连不上时会走默认地址。

## 其他触发场景

（暂无）
