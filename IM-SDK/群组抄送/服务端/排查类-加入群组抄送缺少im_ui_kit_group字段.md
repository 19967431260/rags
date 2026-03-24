---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 群组抄送
platform: 服务端
title: 加入群组抄送缺少im_ui_kit_group字段
root_cause: im_ui_kit_group字段是创建群时通过扩展字段设置的，服务端创建群需要设置serverExtension才能带上该字段。
solution: 服务端创建高级群时使用v2.1接口/im/v2.1/teams，设置serverExtension字段来区分高级群和讨论组。
customers: ['杭州白豪斯出海商业管理有限公司']
source: chat_history
tags: ['IM V10', '群组抄送', 'im_ui_kit_group', 'serverExtension', '高级群', '讨论组']
created: 2025-01-15
updated: 2026-03-23
---

## 问题：加入群组抄送缺少im_ui_kit_group字段

## 问题详情

**现象**：
客户反馈加入群组信息推送中im_ui_kit_group字段和tinfo的9字段（群人数）缺失。

## 排查过程

1. 客户反馈加入群组抄送缺少字段
2. 技术支持确认群成员已满1000个
3. 建议控制台扩容并更新members_limit字段
4. 客户确认已设置上限，问题不是群满
5. 排查发现im_ui_kit_group字段只在创建群时设置扩展字段才会带
6. 更新群信息时不会带此字段
7. 确认服务端v2.1创建接口的serverExtension对应18字段

## 问题原因

im_ui_kit_group字段是创建群时通过扩展字段设置的，服务端创建群需要设置serverExtension才能带上该字段。

## 解决方案

服务端创建高级群时使用v2.1接口/im/v2.1/teams，设置serverExtension字段来区分高级群和讨论组。

## 其他触发场景

（合并时在此处追加）
