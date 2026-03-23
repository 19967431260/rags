---
track_type: 排查类
sub_type: 线上事故
product: IM-SDK
feature: LBS服务
platform: Web
title: lbs.netease.im域名DNS劫持问题
root_cause: 部分运营商网络对lbs.netease.im域名存在DNS劫持
solution: 建议升级SDK至9.20.10版本，或设置defaultLink进行tcp连接
customers: ["中企网动力(北京)科技有限公司"]
source: chat_history
tags: ["LBS", "DNS劫持", "Web", "会话列表"]
created: 2025-06-09
updated: 2025-03-23
---

## 问题：Web lbs.netease.im域名DNS劫持问题

## 问题详情

**现象**：
部分网络环境下lbs.netease.im域名被DNS劫持，解析地址错误，导致会话列表无法加载。

**环境信息**：
- SDK版本：9.6.4
- 网络环境：北京联通/电信

## 排查过程

1. 确认lbs接口报错 → 2. 检查网络环境（北京联通/电信） → 3. 确认SDK版本9.6.4 → 4. 建议升级版本或设置defaultLink

## 问题原因

部分运营商网络对lbs.netease.im域名存在DNS劫持

## 解决方案

建议升级SDK至9.20.10版本，或设置defaultLink进行tcp连接
