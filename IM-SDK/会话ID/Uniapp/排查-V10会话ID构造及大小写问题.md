---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 会话ID
platform: Uniapp
title: V10会话ID构造及大小写问题
root_cause: accountid包含大写字母导致会话ID构造失败
solution: 重新创建帐号，使用纯小写的accountid。会话ID格式：accountid|2|groupId。
customers: ['四川白宇信息科技有限公司']
source: chat_history
tags: ['V10', '会话ID', '191006', '大小写', 'accountid']
created: 2025-01-14
updated: 2026-03-23
---

## 问题：Uniapp V10会话ID构造及大小写问题

## 问题详情

**现象**：
客户使用群组ID构造会话ID时返回191006错误，提示会话不存在。

## 排查过程

1. 客户反馈获取会话报错191006 → 技术支持询问传入参数 → 发现accountid包含大写字母 → 建议重新创建帐号使用小写

## 问题原因

accountid包含大写字母导致会话ID构造失败

## 解决方案

重新创建帐号，使用纯小写的accountid。会话ID格式：accountid|2|groupId。

## 其他触发场景

（合并时在此处追加）
