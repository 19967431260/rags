---
track_type: 排查类
sub_type: 集成类
product: 直播
feature: 转码处理
platform: Server
title: 点播转码模板transConfig格式
root_cause: transConfig需要是JSON array格式，客户直接传了JSON对象
solution: transConfig参数必须使用JSON array格式，如：[{...}]
customers: ['VIP云信-北京汉医健康科技']
source: chat_history
tags: ['点播', '转码模板', 'transConfig', 'JSON格式']
created: 2025-01-13
updated: 2026-03-23
---

## 问题：Server 点播转码模板transConfig格式

## 问题详情

**现象**：
创建点播转码模板时，transConfig参数格式错误导致接口调用失败。

## 排查过程

1. 客户提供参数后接口返回错误。
2. 排查发现transConfig参数格式不正确。

## 问题原因

transConfig需要是JSON array格式，客户直接传了JSON对象

## 解决方案

transConfig参数必须使用JSON array格式，如：[{...}]

## 其他触发场景

（合并时在此处追加）
