---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 反垃圾
platform: 安卓
title: 创建群时返回403 antispam team name错误
root_cause: 群名称命中反垃圾规则
solution: 在云信控制台设置群资料文本不过审，可跳过反垃圾校验。群成员昵称(teamMember)不送审，Nimuser昵称属于用户资料会送审。
customers: ['北京视游互动科技有限公司']
source: chat_history
tags: ['反垃圾', 'antispam', 'team name', '403', '建群']
created: 2025-01-09
updated: 2026-03-23
---

## 问题：安卓 创建群时返回403 antispam team name错误

## 问题详情

**现象**：
创建群时返回{"code":403,"desc":"antispam : team name"}错误，群名称被反垃圾拦截。

## 排查过程

1. 客户反馈创建群报错 → 技术支持确认是群名称命中反垃圾 → 建议控制台设置群资料文本不过审

## 问题原因

群名称命中反垃圾规则

## 解决方案

在云信控制台设置群资料文本不过审，可跳过反垃圾校验。群成员昵称(teamMember)不送审，Nimuser昵称属于用户资料会送审。

## 其他触发场景

（合并时在此处追加）
