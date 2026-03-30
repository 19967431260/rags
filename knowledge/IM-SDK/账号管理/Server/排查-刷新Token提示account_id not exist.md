---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 账号管理
platform: 服务端
title: 刷新Token提示account_id not exist
root_cause: 账号实际未调用注册接口，客户端认为注册成功可能是业务逻辑问题
solution: 确认账号是否真正调用了注册接口，检查业务代码中注册逻辑是否正确执行
customers: ["YOOY语音"]
source: chat_history
tags: ["account_id not exist", "刷新Token", "账号注册", "accid"]
created: 2026-02-02
updated: 2026-03-17
---

## 问题：服务端 刷新Token提示account_id not exist

## 问题详情

**现象**：
客户反馈注册用户后刷新token时提示错误：account_id not exist。经查询发现部分accid在指定appkey下未注册成功，但客户端日志显示有成功有失败。

## 排查过程

1. 查询appkey：608f490437943cdff3b67b30f908911c下accid：9000310 → 未注册
2. 查询另一个appkey：71ce5f691a959a8c38317266d3618ddc → 也未注册
3. 查询accid：9000340 → 在正式key下存在
4. 查询最近7天注册记录 → 没有accid：9000285的注册调用记录

**关键发现**：报错的账号确实都没有注册过，符合预期

## 问题原因

账号实际未调用注册接口，客户端认为注册成功可能是业务逻辑问题

## 解决方案

确认账号是否真正调用了注册接口，检查业务代码中注册逻辑是否正确执行

## 其他触发场景

（暂无）
