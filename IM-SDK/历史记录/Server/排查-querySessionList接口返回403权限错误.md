---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 历史记录
platform: Server
title: querySessionList接口返回403权限错误
root_cause: 未开通服务端会话权限
solution: 需要在控制台IM全局功能里开通服务端会话权限。
customers: ["鱼吼有限公司"]
source: chat_history
tags: ["querySessionList","403","服务端会话","权限开通"]
created: 2026-02-02
updated: 2026-03-17
---

## 问题：Server querySessionList接口返回403权限错误

## 问题详情

**现象**：
调用服务端会话列表查询接口https://api.yunxinapi.com/nimserver/history/querySessionList.action时返回403错误,响应内容为{"code":403,"desc":"func not enable"}。请求参数和鉴权信息均正确。

## 问题原因

未开通服务端会话权限

## 解决方案

需要在控制台IM全局功能里开通服务端会话权限。

## 其他触发场景

