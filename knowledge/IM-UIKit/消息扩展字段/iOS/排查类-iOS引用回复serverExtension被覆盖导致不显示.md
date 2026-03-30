---
track_type: 排查类
sub_type: 使用问题
product: IM-UIKit
feature: 消息扩展字段
platform: iOS
title: iOS引用回复serverExtension被覆盖导致不显示
root_cause: 引用回复功能的数据存储在消息的serverExtension字段中，添加自定义参数时覆盖了这个字段的原有值。
solution: 添加自定义参数时，不能覆盖serverExtension已有的值，需要追加在原有参数后面。或者付费开通高级功能避免此限制。
customers: ['东莞霖感科技有限公司']
source: chat_history
tags: ['iOS', 'UIKit', 'serverExtension', '引用回复', '消息扩展']
created: 2025-01-07
updated: 2026-03-23
---

## 问题：iOS引用回复serverExtension被覆盖导致不显示

## 问题详情

**现象**：
在发送引用回复消息时，如果自定义serverExtension字段，会覆盖系统原有的serverExtension值，导致引用文案不显示。

## 排查过程

1. 客户反馈添加serverExtension后引用文案不显示 → 技术支持确认问题
2. 分析发现回复功能的数据存储在serverExtension中 → 自定义参数不能覆盖已有值

## 问题原因

引用回复功能的数据存储在消息的serverExtension字段中，添加自定义参数时覆盖了这个字段的原有值。

## 解决方案

添加自定义参数时，不能覆盖serverExtension已有的值，需要追加在原有参数后面。或者付费开通高级功能避免此限制。

## 其他触发场景

（合并时在此处追加）
