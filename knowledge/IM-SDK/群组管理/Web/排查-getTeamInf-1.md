---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 群组管理
platform: Web
title: getTeamInfo接口调用问题
root_cause: getTeamInfo的teamType参数传值错误，传了2(超大群)而不是1(普通群)
solution: getTeamInfo的teamType参数，普通群用1，超大群用2
customers: ["湖南登时互动网络科技有限公司"]
source: chat_history
tags: ["getTeamInfo", "teamType", "群组", "Web"]
created: 2025-02-21
updated: 2026-03-20
---

## 问题：Web getTeamInfo接口调用问题

## 问题详情

**现象**：
客户调用getTeamInfo接口获取群组信息，但返回结果异常。

## 排查过程

1. 确认SDK版本
2. 检查apiVersion参数
3. 询问teamType传值 → 客户传的是2
4. 确认问题 → 2是超大群，应该用1

## 问题原因

getTeamInfo的teamType参数传值错误，传了2(超大群)而不是1(普通群)

## 解决方案

getTeamInfo的teamType参数，普通群用1，超大群用2

## 其他触发场景
- [Web] getTeamInfo接口调用问题，来源：['湖南登时互动网络科技有限公司']，2026-03-20
- [Web] getTeamInfo接口调用问题，来源：['湖南登时互动网络科技有限公司']，2026-03-20

