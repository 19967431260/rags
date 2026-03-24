---
track_type: 排查类
sub_type: 使用问题
product: 网易会议
feature: 服务端API
platform: 服务端
title: 创建预约会议type=3时参数错误
root_cause: 预约会议（type=3）需要传递starttime和endtime参数，客户未传递导致参数校验失败。
solution: 创建预约会议时，需在请求体中传递scheduleTime.starttime和scheduleTime.endtime参数指定会议开始和结束时间。
customers: ['乌鲁木齐小才人教育科技有限公司']
source: chat_history
tags: ['网易会议', '创建会议', '预约会议', '参数错误']
created: 2025-01-07
updated: 2026-03-23
---

## 问题：服务端 创建预约会议type=3时参数错误

## 问题详情

**现象**：
客户调用创建会议接口时，type传3报错参数错误，传2正常。

## 排查过程

1. 客户反馈type=3创建会议报错
2. 查看requestId发现scheduleTime为illegal
3. 确认type=3为预约会议，需要传递starttime和endtime
4. 客户确认未传时间参数

## 问题原因

预约会议（type=3）需要传递starttime和endtime参数，客户未传递导致参数校验失败。

## 解决方案

创建预约会议时，需在请求体中传递scheduleTime.starttime和scheduleTime.endtime参数指定会议开始和结束时间。

## 其他触发场景

（合并时在此处追加）
