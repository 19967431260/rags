---
track_type: 排查类
sub_type: 配置开通咨询
product: 短信
feature: 国际短信
platform: 通用
title: 阿尔及利亚短信发送forbid country限制
root_cause: 控制台设置了发送区域限制，导致部分国家无法发送
solution: 在控制台短信设置中检查并调整发送区域限制配置。
customers: ["时间在线"]
source: chat_history
tags: ["国际短信", "forbid country", "区域限制", "阿尔及利亚"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：阿尔及利亚短信发送forbid country限制

## 问题详情

**现象**：
发送短信到阿尔及利亚时接口返回forbid country，询问如何解除限制。

**环境信息**：
- 平台：通用

## 排查过程

1. 客户反馈发送阿尔及利亚短信返回forbid country
2. 检查控制台设置，发现可能限制了区域发送

## 根因分析

控制台设置了发送区域限制，导致部分国家无法发送

## 解决方案

在控制台短信设置中检查并调整发送区域限制配置。

## 其他触发场景

（无）
