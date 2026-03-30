---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 登录鉴权
platform: Uniapp
title: IM登录密码错误导致连接失败
root_cause: appkey、account、token三者不匹配导致登录鉴权失败
solution: 登录鉴权失败说明appkey、account、token三者不匹配。如不记得正确token，可通过服务端接口重新刷新token。文档：https://doc.yunxin.163.com/messaging/server-apis/DUxNDQ3NjA
customers: ['云南铁宝机械设备销售有限责任公司']
source: chat_history
tags: ['Uniapp', '登录', '密码错误', '鉴权', 'token']
created: 2025-01-15
updated: 2026-03-23
---

## 问题：Uniapp IM登录密码错误导致连接失败

## 问题详情

**现象**：
客户反馈修改套餐后连接不成功，一直提示密码错误，确认代码未改动。

## 排查过程

1. 客户反馈改套餐后连接失败
2. 查看console日志发现密码错误
3. 确认appkey、account、token三者不匹配
4. 建议重新刷新token

## 问题原因

appkey、account、token三者不匹配导致登录鉴权失败

## 解决方案

登录鉴权失败说明appkey、account、token三者不匹配。如不记得正确token，可通过服务端接口重新刷新token。文档：https://doc.yunxin.163.com/messaging/server-apis/DUxNDQ3NjA

## 其他触发场景

（合并时在此处追加）
