---
track_type: 排查类
sub_type: 客户环境问题
product: NERoom
feature: 白板服务
platform: Web
title: 抓包代理导致白板PPT打不开
root_cause: 抓包代理截获SDK包导致RTC连接失败
solution: 抓包代理实现方式可能影响SDK连接，报错显示连不上RTC服务器
customers: ["智慧树"]
source: chat_history
tags: ["白板", "抓包", "代理", "RTC", "连接失败"]
created: 2025-11-12
updated: 2026-03-20
---

## 问题：Web 抓包代理导致白板PPT打不开

## 问题详情

**现象**：
测试开了抓包代理后web白板PPT文件打不开，提示错误。

## 排查过程

1. 分析错误信息
2. 确认网络连接
**关键发现**：sdk的包被截获，rtc连不上服务器，白板加入房间超时失败

## 问题原因

抓包代理截获SDK包导致RTC连接失败

## 解决方案

抓包代理实现方式可能影响SDK连接，报错显示连不上RTC服务器

## 其他触发场景

