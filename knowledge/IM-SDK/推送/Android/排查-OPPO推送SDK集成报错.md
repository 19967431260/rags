---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 推送
platform: Android
title: OPPO推送SDK集成报错
root_cause: 缺少OPPO推送SDK所需的apache库依赖
solution: 集成3个apache库：httpclient、httpcore、httpmime
customers: ['北京睿圣网络科技有限公司']
source: chat_history
tags: ['OPPO推送', 'apache库', '集成', 'Android', '3.1.0']
created: 2025-01-17
updated: 2026-03-23
---

## 问题：Android OPPO推送SDK集成报错

## 问题详情

**现象**：
客户使用IM SDK 9.6.3版本，集成OPPO推送SDK 3.1.0出现报错。

## 排查过程

1. 确认OPPO推送SDK版本正确 → 发现缺少apache库\n2. 需要补充集成3个apache依赖库

## 问题原因

缺少OPPO推送SDK所需的apache库依赖

## 解决方案

集成3个apache库：httpclient、httpcore、httpmime

## 其他触发场景

（合并时在此处追加）
