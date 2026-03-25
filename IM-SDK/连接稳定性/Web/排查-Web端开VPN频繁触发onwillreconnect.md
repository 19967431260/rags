---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 连接稳定性
platform: Web
title: Web端开VPN频繁触发onwillreconnect
root_cause: VPN导致DNS解析问题或网络连接不稳定，影响SDK与服务器的连接。
solution: 建议更换VPN节点，选择时延较小的地区节点，确保能正常访问中国公网。
customers: ["北京鑫互联"]
source: chat_history
tags: ["onwillreconnect", "VPN", "Web", "连接重连", "DNS解析"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：Web端开VPN频繁触发onwillreconnect

## 问题详情

**现象**：
客户反馈Web端开启VPN后，每隔一分钟左右就会触发一次onwillreconnect重连事件。

**环境信息**：
- 平台：Web

## 排查过程

1. 确认问题仅在开启VPN时出现 → 判断为VPN导致的网络问题
2. 客户关闭VPN测试 → 问题消失，确认是VPN导致
3. 分析原因 → VPN可能导致DNS解析问题或连接不稳定

## 根因分析

VPN导致DNS解析问题或网络连接不稳定，影响SDK与服务器的连接。

## 解决方案

建议更换VPN节点，选择时延较小的地区节点，确保能正常访问中国公网。

## 其他触发场景

（无）
