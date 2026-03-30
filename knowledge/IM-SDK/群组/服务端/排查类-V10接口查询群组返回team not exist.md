---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 群组
platform: 服务端
title: V10接口查询群组返回team not exist
root_cause: 客户数据库ID字段类型太小，无法存储云信返回的大整数team_id，导致数据截断
solution: 使用IM V10服务端API时，群组ID(team_id)是大整数类型，需要确保数据库ID字段足够大（建议使用bigint/long类型）来存储完整的team_id，避免数据截断导致查询失败。
customers: ['深圳市希楠电子科技有限公司']
source: chat_history
tags: ['IM-SDK', 'V10', 'team not exist', 'team_id', '数据库', '108404']
created: 2025-01-13
updated: 2026-03-23
---

## 问题：V10接口查询群组返回team not exist

## 问题详情

**现象**：
客户使用IM V10服务端接口查询群组时返回{"code":108404,"msg":"team not exist"}，但实际群组是存在的。

## 排查过程

1. 客户调用/v2/teams/4294967295接口返回team not exist
2. 技术支持询问appkey后发现是测试账号已过期
3. 客户申请延期后问题解决
4. 后续客户发现创建的3个群组返回的team_id都一样
5. 最终发现是客户数据库设计ID值太小导致

## 问题原因

客户数据库ID字段类型太小，无法存储云信返回的大整数team_id，导致数据截断

## 解决方案

使用IM V10服务端API时，群组ID(team_id)是大整数类型，需要确保数据库ID字段足够大（建议使用bigint/long类型）来存储完整的team_id，避免数据截断导致查询失败。

## 其他触发场景

（合并时在此处追加）
