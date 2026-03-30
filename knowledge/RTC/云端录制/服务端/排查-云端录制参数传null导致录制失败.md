---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 云端录制
platform: 服务端
title: 云端录制参数传null导致录制失败
root_cause: 其他参数传null导致录制失败，应该不传而非传null
solution: 不设置的参数直接不传，不要传null值
customers: ["杭州帆特科技有限公司"]
source: chat_history
tags: ["云端录制", "参数传递", "null", "录制失败"]
created: 2026-02-12
updated: 2026-03-17
---

## 问题：服务端 云端录制参数传null导致录制失败

## 问题详情

**现象**：
调用/v2/api/cloudrecord/submit创建云端录制，只传cid和recordType参数，其他参数未设置。接口返回成功并有taskId，但查询录制文件为空，state状态为0(初始状态)。

## 排查过程

1. 检查录制任务创建 → 接口返回成功，有taskId
2. 查询录制状态 → state为0(初始状态)
3. 检查参数传递方式 → 发现客户传的是null而非不传

**关键发现**：后台日志显示参数都是null，传null会导致录制失败

## 问题原因

其他参数传null导致录制失败，应该不传而非传null

## 解决方案

不设置的参数直接不传，不要传null值

## 其他触发场景
