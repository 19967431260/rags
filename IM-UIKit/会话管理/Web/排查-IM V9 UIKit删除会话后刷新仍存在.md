---
track_type: 排查类
sub_type: 使用问题
product: IM-UIKit
feature: 会话管理
platform: Web
title: IM V9 UIKit删除会话后刷新仍存在
root_cause: 删除会话只删除本地，未删除漫游消息，下次登录SDK根据漫游消息重新生成会话
solution: UIKit删除会话不删除漫游，如需彻底删除需配合服务端接口删除漫游消息。insertLocalSession/updateLocalSession接口在UIKit中无法使用，因为UIKit不开本地DB。
customers: ['上海超旺信息科技有限公司']
source: chat_history
tags: ['IM V9', 'UIKit', '删除会话', '漫游消息', 'indexedDB']
created: 2025-01-06
updated: 2026-03-23
---

## 问题：Web IM V9 UIKit删除会话后刷新仍存在

## 问题详情

**现象**：
会话列表点击删除会话按钮后显示deleteStickTopSession取消云端置顶会话失败。列表显示已删除，但刷新网页后刚刚删除的会话还在列表里。使用V9版本UIKit。

## 排查过程

1. 确认删除操作执行 → 发现删除会话可能没删除漫游
2. 分析会话生成机制 → 下次登录还会下发漫游消息，SDK重新生成会话

## 问题原因

删除会话只删除本地，未删除漫游消息，下次登录SDK根据漫游消息重新生成会话

## 解决方案

UIKit删除会话不删除漫游，如需彻底删除需配合服务端接口删除漫游消息。insertLocalSession/updateLocalSession接口在UIKit中无法使用，因为UIKit不开本地DB。

## 其他触发场景

（合并时在此处追加）
