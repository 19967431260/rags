---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 群组
platform: 服务端
title: 转让群主返回account_id not a member
root_cause: 被转让的账号虽然被邀请加入群组，但未实际加入群组，不在群成员列表中
solution: 转让群主时，new_owner_account_id必须是已经在群中的成员。被邀请(invite_account_ids)但未实际加入的用户不能直接被转让为群主，需要先确认对方已加入群组。
customers: ['深圳市希楠电子科技有限公司']
source: chat_history
tags: ['IM-SDK', '转让群主', 'account_id not a member', '群成员']
created: 2025-01-13
updated: 2026-03-23
---

## 问题：转让群主返回account_id not a member

## 问题详情

**现象**：
客户使用服务端接口转让群主时返回account_id not a member错误。

## 排查过程

1. 客户调用transfer_owner接口无返回值
2. 尝试添加管理员时返回account_id not a member
3. 技术支持检查发现new_owner_account_id不在群里
4. 客户确认该账号是建群时invite_account_ids邀请的

## 问题原因

被转让的账号虽然被邀请加入群组，但未实际加入群组，不在群成员列表中

## 解决方案

转让群主时，new_owner_account_id必须是已经在群中的成员。被邀请(invite_account_ids)但未实际加入的用户不能直接被转让为群主，需要先确认对方已加入群组。

## 其他触发场景

（合并时在此处追加）
