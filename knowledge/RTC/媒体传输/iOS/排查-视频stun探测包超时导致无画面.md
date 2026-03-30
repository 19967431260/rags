---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 媒体传输
platform: iOS
title: 视频stun探测包超时导致无画面
root_cause: stun探测包用于检测UDP协议连通性，超时原因可能是路由器转发长度限制、防火墙拦截UDP端口等网络问题。
solution: 1. 确认防火墙已开通云信媒体服务器的UDP端口段（4X00~4X09，每台开10个端口）。2. 检查网络环境是否对UDP协议有限制。3. 如需详细分析，建议提供网络抓包数据。
customers: ["平安银行"]
source: chat_history
tags: ["iOS", "视频", "stun", "UDP", "端口", "Unwritable", "网络"]
created: 2026-01-06
updated: 2026-03-15
---

## 问题：iOS 视频stun探测包超时导致无画面

## 问题详情

**现象**：
iOS端通话中出现视频无画面问题，后台录制文件中没有客户的视频流但有音频流。日志显示Unwritable after 5 ping failures和Timed out after等报错。

## 排查过程

1. 搜索日志关键字Unwritable after、Timed out after
2. 搜索RequestPublish找到video对应的udpip和port端口
3. 确认连接的UDP端口（如4202）
**关键发现**：stun探测包发送到特定UDP端口（如45.65.23.x:4202）超时，无法建立视频媒体连接。

## 问题原因

stun探测包用于检测UDP协议连通性，超时原因可能是路由器转发长度限制、防火墙拦截UDP端口等网络问题。

## 解决方案

1. 确认防火墙已开通云信媒体服务器的UDP端口段（4X00~4X09，每台开10个端口）。2. 检查网络环境是否对UDP协议有限制。3. 如需详细分析，建议提供网络抓包数据。

## 其他触发场景

- [iOS] 视频stun探测包超时导致无画面，来源：['平安银行']，2026-03-15
（合并时在此处追加）
- [iOS] 视频stun探测包超时导致无画面，来源：['平安银行']，2026-03-15
