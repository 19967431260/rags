---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 长连接
platform: 通用
title: IM长连接域名weblink偶发超时排查
root_cause: 网络链路存在偶发丢包，域名解析IP动态变化
solution: 建议客户尽快支持IPv6解析，后续IPv6可能更普及；同时排查网络链路稳定性
customers: ['ISV云信-北京易诚互动-华侨银行']
source: chat_history
tags: ['weblink', '长连接', '超时', '网络丢包', 'IPv6']
created: 2025-01-10
updated: 2026-03-23
---

## 问题：通用 IM长连接域名weblink偶发超时排查

## 问题详情

**现象**：
客户反馈IM长连接域名weblink接口偶发超时，网络团队排查发现部分请求没有回包，从防火墙发现丢包现象。

## 排查过程

1. 客户网络团队检查防火墙发现部分请求无回包
2. 确认域名解析IP可能有多个，存在切换
3. 排查网络链路，发现偶发超时问题
4. 建议客户尽快支持IPv6解析

## 问题原因

网络链路存在偶发丢包，域名解析IP动态变化

## 解决方案

建议客户尽快支持IPv6解析，后续IPv6可能更普及；同时排查网络链路稳定性

## 其他触发场景

（合并时在此处追加）
