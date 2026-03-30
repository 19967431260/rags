---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 群资料
platform: Android
title: updateTeamInfo返回forbidden错误
root_cause: 客户第三方回调服务(https://zt-gateway-test.xunfeng.cn/rest/b/zt/im-service/nauth/api/1.0/yun-xin/im/login/callback)拦截了更新群资料的请求
solution: 检查第三方回调服务的拦截逻辑，确认是否对群资料更新操作进行了限制。
customers: ['巽风科技']
source: chat_history
tags: ['forbidden', 'updateTeamInfo', '群公告', '第三方回调']
created: 2025-01-14
updated: 2026-03-23
---

## 问题：Android updateTeamInfo返回forbidden错误

## 问题详情

**现象**：
客户调用v2TeamService.updateTeamInfo方法更新群公告，V2NIMFailureCallback返回callback forbidden。

## 排查过程

1. 确认当前用户是群主
2. 检查updateTeamInfoParams只放了announcement
3. 排查发现是客户第三方回调服务拦截了请求

## 问题原因

客户第三方回调服务(https://zt-gateway-test.xunfeng.cn/rest/b/zt/im-service/nauth/api/1.0/yun-xin/im/login/callback)拦截了更新群资料的请求

## 解决方案

检查第三方回调服务的拦截逻辑，确认是否对群资料更新操作进行了限制。

## 其他触发场景

（合并时在此处追加）
