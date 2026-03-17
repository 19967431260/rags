---
track_type: 排查类
sub_type: 使用问题
product: IM-UIKit
feature: 会话列表
platform: Uniapp
title: V9和V10 insertSessionActive参数格式差异
root_cause: V9和V10的insertSessionActive接口参数格式不同，V9传入群id，V10传入整条会话记录。
solution: 查看API文档了解V9和V10格式差异。insertSessionActive接口本身插入的是空会话，最新一条消息为空是正常的。V9版本没有接口直接修改未读数。
tags: ["insertSessionActive", "V9", "V10", "参数格式", "UIKit"]
customers: ["厦门亿佳链鑫科技有限公司"]
source: chat_history
created: 2026-02-06
updated: 2026-03-17
---

## 问题：Uniapp V9和V10 insertSessionActive参数格式差异

## 问题详情

**现象**：
在V9版本使用insertSessionActive时传入V10格式参数，导致返回数据不匹配。添加的会话数据与返回的数据对不上，最新一条消息为空。

**环境信息**：
- 平台：Uniapp
- UIKit版本：V9

## 排查过程

**关键发现**：V9和V10的insertSessionActive接口参数格式不同

## 问题原因

V9和V10的insertSessionActive接口参数格式不同，V9传入群id，V10传入整条会话记录。

## 解决方案

查看API文档了解V9和V10格式差异。insertSessionActive接口本身插入的是空会话，最新一条消息为空是正常的。V9版本没有接口直接修改未读数。

## 其他触发场景

