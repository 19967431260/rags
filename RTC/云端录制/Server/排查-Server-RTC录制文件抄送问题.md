---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 云端录制
platform: Server
title: RTC录制文件抄送问题
root_cause: 
solution: 抄送正常，建议客户检查回调接收端是否正常处理
customers: ["浙江惠瀜"]
source: chat_history
tags: ["RTC", "录制", "抄送", "回调"]
created: 2025-11-05
updated: 2026-03-20
---

## 问题：Server RTC录制文件抄送问题

## 问题详情

**现象**：
客户反馈有录制但没有收到回调，房间号57747971835956。

## 排查过程

1. 查询录制任务
2. 检查抄送记录
**关键发现**：抄送成功，httpCode[200]，回调地址https://sign.hrfax.cn/nim/callback

## 问题原因

暂无根因分析

## 解决方案

抄送正常，建议客户检查回调接收端是否正常处理

## 其他触发场景

