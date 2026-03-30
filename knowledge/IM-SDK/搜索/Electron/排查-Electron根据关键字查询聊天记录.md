---
track_type: 排查类
sub_type: 配置开通咨询
product: IM-SDK
feature: 搜索
platform: Electron
title: Electron根据关键字查询聊天记录
root_cause: 没有开启云端检索功能的权限。
solution: 在控制台后台开启云端检索功能的权限。
customers: ['深圳市君莫管文化传媒有限公司']
source: chat_history
tags: ['Electron', '搜索', '聊天记录', 'searchCloudMessages', '权限']
created: 2024-12-31
updated: 2026-03-23
---

## 问题：Electron Electron根据关键字查询聊天记录

## 问题详情

**现象**：
客户咨询Electron桌面端如何根据关键字查询聊天记录，使用哪个接口。

## 排查过程

1. 客户询问如何根据关键字查询聊天记录
2. 技术支持提供文档链接
3. 另一客户询问v10本地electron api什么时候支持搜索聊天记录和会话
4. 技术支持确认10.7.0版本支持
5. 客户反馈v2.messageService.searchCloudMessages全文搜索云端历史消息报错
6. 技术支持查看后发现是没有权限导致
7. 建议后台开启云端检索功能权限

## 问题原因

没有开启云端检索功能的权限。

## 解决方案

在控制台后台开启云端检索功能的权限。

## 其他触发场景

（合并时在此处追加）
