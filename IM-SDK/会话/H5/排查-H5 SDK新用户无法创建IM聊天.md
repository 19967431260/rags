---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 会话
platform: H5
title: H5 SDK新用户无法创建IM聊天
root_cause: ""
solution: 需要全局拦截console对象输出内容记录到本地并上传业务服务器；建议先在测试环境复现问题
customers: ["深圳招银国际"]
source: chat_history
tags: ["H5","创建会话","新用户","console"]
created: 2025-02-08
updated: 2025-03-20
---

## 问题：H5 H5 SDK新用户无法创建IM聊天

## 问题详情

**现象**：
UAT环境新设备或新用户无法创建IM聊天，服务端接口报错。

## 排查过程

1. 确认使用H5 SDK接入 → 确认接入方式
2. 需要全局拦截console对象记录日志 → 提供排查方案
3. 建议测试环境复现获取console日志 → 建议复现

## 解决方案

需要全局拦截console对象输出内容记录到本地并上传业务服务器；建议先在测试环境复现问题。

## 其他触发场景

