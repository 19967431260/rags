---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 用户管理
platform: iOS
title: fetchUserInfos获取用户信息无回调
root_cause: 客户代码中频繁调用NIMSDK.shared().userManager.userInfo(uid)本地查询接口，导致性能问题，可能影响fetchUserInfos的正常回调处理。
solution: 建议优化会话列表获取逻辑，不要一次性查询所有会话的用户资料，可以分页查询（先查10-20条），并做内存缓存，避免每次都去数据库查询。
customers: ['杭州晶达网络科技有限公司']
source: chat_history
tags: ['fetchUserInfos', 'userInfo', '用户信息', '性能优化', 'iOS', '9.19.0']
created: 2025-01-21
updated: 2026-03-23
---

## 问题：fetchUserInfos获取用户信息无回调

## 问题详情

**现象**：
客户反馈通过NIMSDK.shared().userManager.fetchUserInfos获取用户信息，callback里没有返回信息。

## 排查过程

1. 客户反馈iu-p-281账户获取不到用户信息
2. 技术支持查看日志发现fetchUserInfos请求返回200，但SDK日志不打印具体返回结果
3. 发现日志中有海量的NIMUserManagerWrapper userInfo:查询本地用户资料的调用，1ms内有几十次，日志中有几十万次
4. 客户确认获取会话列表时会遍历会话id调用userInfo方法，频繁触发

## 问题原因

客户代码中频繁调用NIMSDK.shared().userManager.userInfo(uid)本地查询接口，导致性能问题，可能影响fetchUserInfos的正常回调处理。

## 解决方案

建议优化会话列表获取逻辑，不要一次性查询所有会话的用户资料，可以分页查询（先查10-20条），并做内存缓存，避免每次都去数据库查询。

## 其他触发场景

（合并时在此处追加）
