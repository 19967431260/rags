---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 会话管理
platform: Web
title: Web端删除会话后刷新仍存在
root_cause: deleteType参数使用不正确，且deleteSession和deleteLocalSession参数混淆
solution: 使用deleteType为localAndRemote，注意deleteSession和deleteLocalSession参数一个是id一个是to
customers: ["VIP云信-武汉自由无限科技有限公司"]
source: chat_history
tags: ["Web", "删除会话", "deleteSession", "deleteType", "onsessions"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：Web端删除会话后刷新仍存在

## 问题详情

**现象**：
Web端调用deleteSession和deleteLocalSession删除会话，删除成功后刷新页面会话仍存在

**环境信息**：
- 平台：Web

## 排查过程

1. 客户反馈删除会话后刷新仍存在
2. 确认使用onsessions通知获取会话列表
3. 发现deleteType参数使用不正确
4. 建议使用localAndRemote删除类型

## 根因分析

deleteType参数使用不正确，且deleteSession和deleteLocalSession参数混淆

## 解决方案

使用deleteType为localAndRemote，注意deleteSession和deleteLocalSession参数一个是id一个是to

## 其他触发场景

（无）
