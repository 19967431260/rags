---
track_type: 排查类
sub_type: 集成类
product: IM-UIKit
feature: 消息展示
platform: Uniapp
title: Uniapp消息左右显示异常与accid大小写问题
root_cause: 云信accid不支持大写字母，导致消息发送方识别异常
solution: 云信accid不能包含大写字母，需要使用纯小写accid。修改accid为小写后可解决消息左右显示异常问题。
customers: ['云南铁宝机械设备销售有限责任公司']
source: chat_history
tags: ['Uniapp', 'accid', '大小写', '消息显示']
created: 2025-01-04
updated: 2026-03-23
---

## 问题：Uniapp Uniapp消息左右显示异常与accid大小写问题

## 问题详情

**现象**：
客户使用Uniapp开发，发消息后消息显示在左侧（接收方位置）而非右侧（发送方位置），退出重进才正常。

## 排查过程

1. 客户反馈发送的消息显示在左侧而非右侧
2. 技术支持询问是否必现
3. 确认是必现问题
4. 询问accid是否有大写
5. 客户确认accid有大写
6. 告知accid不能有大写

## 问题原因

云信accid不支持大写字母，导致消息发送方识别异常

## 解决方案

云信accid不能包含大写字母，需要使用纯小写accid。修改accid为小写后可解决消息左右显示异常问题。

## 其他触发场景

（合并时在此处追加）
