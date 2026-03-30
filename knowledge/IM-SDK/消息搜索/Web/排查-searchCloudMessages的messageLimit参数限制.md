---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息搜索
platform: Web
title: searchCloudMessages的messageLimit参数限制
root_cause: 文档描述有误，服务器限制。云端检索耗性能，故限制返回数量
solution: 带conversationLimit时msgLimit最大10，不带时最大100。如需更多数据，按时间分页遍历
customers: ['成都瑞安云科技股份有限公司']
source: chat_history
tags: ['searchCloudMessages', 'messageLimit', 'conversationLimit', '云端检索', '分页']
created: 2025-01-08
updated: 2026-03-23
---

## 问题：Web searchCloudMessages的messageLimit参数限制

## 问题详情

**现象**：
文档描述messageLimit传0表示无限制，但实际传0报错，传1-10可以，超过10也报错

## 排查过程

1. 测试发现msgLimit最大为10
2. 进一步测试发现带conversationLimit时是按会话维度检索(协议30-26)，msgLimit最大10
3. 不带conversationLimit时是按消息维度检索(协议30-27)，msgLimit最大100

## 问题原因

文档描述有误，服务器限制。云端检索耗性能，故限制返回数量

## 解决方案

带conversationLimit时msgLimit最大10，不带时最大100。如需更多数据，按时间分页遍历

## 其他触发场景

（合并时在此处追加）
