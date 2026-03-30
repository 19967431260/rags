---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 本地存储
platform: Web
title: 不同SDK版本共用IndexDB导致阻塞
root_cause: 不同版本SDK共用同一域名导致IndexDB写入冲突阻塞
solution: 升级SDK到统一版本（9.11+），新版本已解决同一版本无此问题
customers: ['政采云']
source: chat_history
tags: ['IndexDB', 'SDK版本', '阻塞', 'Web']
created: 2025-01-03
updated: 2026-03-23
---

## 问题：Web 不同SDK版本共用IndexDB导致阻塞

## 问题详情

**现象**：
采小蜜使用SDK 7.2，其他页面使用9.11，域名都使用www后往一个IndexDB写数据导致阻塞

## 排查过程

1. 确认问题场景 → 两个不同版本SDK共用同一域名
2. 分析IndexDB状态 → open count为2
3. 验证问题 → 客户复现确认阻塞

## 问题原因

不同版本SDK共用同一域名导致IndexDB写入冲突阻塞

## 解决方案

升级SDK到统一版本（9.11+），新版本已解决同一版本无此问题

## 其他触发场景

（合并时在此处追加）
