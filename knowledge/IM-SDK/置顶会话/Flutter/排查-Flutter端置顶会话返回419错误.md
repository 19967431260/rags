---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 置顶会话
platform: Flutter
title: Flutter端置顶会话返回419错误
root_cause: shouldSyncStickTopSessionInfos参数未设置为true，导致客户端无法从服务端同步置顶会话列表，无法查看已置顶会话，也无法取消置顶来释放配额
solution: 在NIMSDKOptions中设置shouldSyncStickTopSessionInfos为true，开启置顶会话列表同步功能。置顶会话上限为100个，超过后需取消已有置顶才能新增。
customers: ['山东鲸鱼']
source: chat_history
tags: ['419', 'addStickTopSession', '置顶会话', 'Flutter', 'shouldSyncStickTopSessionInfos']
created: 2025-01-09
updated: 2026-03-23
---

## 问题：Flutter Flutter端置顶会话返回419错误

## 问题详情

**现象**：
用户在使用Flutter SDK时，调用addStickTopSession方法置顶会话返回419错误，同时queryStickTopSession查询置顶列表返回0条数据。

## 排查过程

1. 检查日志发现addStickTopSession返回419错误码
2. 确认419错误表示置顶会话数量超过上限100个
3. 但用户反馈queryStickTopSession返回0条数据，无法看到已置顶会话
4. 建议检查NIMSDKOptions中的shouldSyncStickTopSessionInfos参数是否设置为true
5. 该参数用于控制是否从服务端同步置顶会话列表到客户端

## 问题原因

shouldSyncStickTopSessionInfos参数未设置为true，导致客户端无法从服务端同步置顶会话列表，无法查看已置顶会话，也无法取消置顶来释放配额

## 解决方案

在NIMSDKOptions中设置shouldSyncStickTopSessionInfos为true，开启置顶会话列表同步功能。置顶会话上限为100个，超过后需取消已有置顶才能新增。

## 其他触发场景

（合并时在此处追加）
