---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 资源下载
platform: 通用
title: CDN IP动态调度导致防火墙拦截
root_cause: CDN智能调度系统会动态新增IP，客户网络需要域名+IP放行
solution: 方案1：额外付费定制固定IP解析入口；方案2：做DNS拨测定期更新防火墙
customers:
  - 海康华安
source: chat_history
tags:
  - CDN
  - IP调度
  - 防火墙
  - DNS解析
created: '2025-06-16'
updated: '2025-03-23'
---

## 问题：通用 CDN IP动态调度导致防火墙拦截

## 问题详情

**现象**：
阿里云拨测工具解析不到112.83.129.63这个IP，但请求nim-nosdn.netease.im会到该IP，被防火墙拦截

**排查过程**：

1. 确认IP归属 → 是云信CDN的IP
2. 分析原因 → CDN智能调度系统会随时新增IP
3. 确认问题 → DNS服务商未及时更新

**关键发现**：CDN智能调度系统会动态新增IP，客户网络需要域名+IP放行

## 问题原因

CDN智能调度系统会动态新增IP，客户网络需要域名+IP放行

## 解决方案

方案1：额外付费定制固定IP解析入口；方案2：做DNS拨测定期更新防火墙
