---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 好友管理
platform: Android
title: 添加好友报错191004 invalid parameter
root_cause: 用户使用当前登录账号添加自己为好友，SDK本地校验不允许自己加自己
solution: 不能添加自己为好友，需要检查业务逻辑，确保添加好友时传入的accid不是当前登录用户的accid
customers: ["联通在线信息科技有限公司"]
source: chat_history
tags: ["191004","addFriend","参数校验","好友管理","V2NIMFriendAddParams"]
created: 2026-02-02
updated: 2026-03-17
---

## 问题：Android 添加好友报错191004 invalid parameter

## 问题详情

**现象**：
使用V2NIMFriendAddParams添加好友时报错191004，错误信息为invalid parameter

**复现步骤**：
1. 调用addFriend接口添加好友
2. 传入V2NIMFriendAddMode.V2NIM_FRIEND_MODE_TYPE_ADD模式

## 排查过程

1. 检查服务器记录 → 服务器上没有相关记录，判断为本地校验异常
2. 要求客户提供登录用户accid和被添加用户accid → 发现登录用户accid和被添加用户accid相同，都是7dcfd506e4ffe9b4b079

**关键发现**：用户尝试添加自己为好友，触发本地参数校验失败

## 问题原因

用户使用当前登录账号添加自己为好友，SDK本地校验不允许自己加自己

## 解决方案

不能添加自己为好友，需要检查业务逻辑，确保添加好友时传入的accid不是当前登录用户的accid

## 其他触发场景

