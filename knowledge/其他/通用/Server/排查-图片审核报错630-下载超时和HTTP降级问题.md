---
track_type: 排查类
sub_type: 使用问题
product: 其他
feature: 通用
platform: Server
title: 图片审核报错630-下载超时和HTTP降级问题
root_cause: 首次下载超时，重试降级HTTP策略与客户资源不兼容
solution: 调整重试策略，去掉降级HTTP的策略，仍然使用HTTPS下载；已配置完成
customers: ['wooplus']
source: chat_history
tags: ['图片审核', '630', '下载超时', 'HTTP', '反垃圾']
created: 2025-01-09
updated: 2026-03-23
---

## 问题：服务端 图片审核报错630-下载超时和HTTP降级问题

## 问题详情

**现象**：
对接图片安全识别时接口报630错误。原因是首次下载超时2.5s，重试降级到HTTP协议，但客户资源不支持HTTP访问返回403。

## 排查过程

1. 客户反馈630错误 → 客服排查发现首次下载超时
2. 检查日志发现重试降级到HTTP后返回403
3. 确认客户资源不支持HTTP协议头访问

## 问题原因

首次下载超时，重试降级HTTP策略与客户资源不兼容

## 解决方案

调整重试策略，去掉降级HTTP的策略，仍然使用HTTPS下载；已配置完成

## 其他触发场景

（合并时在此处追加）
