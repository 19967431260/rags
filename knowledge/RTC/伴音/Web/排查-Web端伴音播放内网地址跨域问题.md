---
track_type: 排查类
sub_type: 集成类
product: RTC
feature: 伴音
platform: Web
title: Web端伴音播放内网地址跨域问题
root_cause: 内网地址跨域限制，SDK无法处理
solution: 使用正式域名访问音频资源，或在NG配置跨域头
customers: ["杭州银行"]
source: chat_history
tags: ["伴音", "跨域", "内网地址", "Web"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：Web Web端伴音播放内网地址跨域问题

## 问题详情

**现象**：
音视频伴音使用内网URL地址报错，fetch请求后转blob可正常播放。

**环境信息**：
- 平台：Web

## 排查过程

1. 确认地址类型 → 内网地址
2. 分析报错 → 跨域问题
3. 尝试解决 → 需要使用正式域名

**关键发现**：内网地址跨域限制，SDK无法处理

## 问题原因

内网地址跨域限制，SDK无法处理

## 解决方案

使用正式域名访问音频资源，或在NG配置跨域头

## 其他触发场景

（无）
