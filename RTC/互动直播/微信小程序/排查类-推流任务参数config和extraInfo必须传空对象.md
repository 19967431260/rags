---
track_type: 排查类
sub_type: 测试问题
product: RTC
feature: 互动直播
platform: 微信小程序
title: 推流任务参数config和extraInfo必须传空对象
root_cause: SDK会校验config和extraInfo参数，即使不配置也需要传空对象，文档未明确说明
solution: 调用addTasks时，config和extraInfo即使不配置也要传空对象：config:{}, extraInfo:''
customers: ['智诚科创网络技术服务有限公司上海分公司']
source: chat_history
tags: ['互动直播', '推流任务', '参数校验', '文档问题']
created: 2025-01-08
updated: 2026-03-23
---

## 问题：推流任务参数config和extraInfo必须传空对象

## 问题详情

**现象**：
客户反馈addTasks接口文档标注config和extraInfo为非必填，但实际不传会报错。

## 排查过程

1. 客户反馈参数问题 → 确认config和extraInfo为文档标注的非必填项
2. 实际测试 → SDK会校验这两个参数
3. 确认解决方案 → 即使不配置也需要传空对象
**关键发现**：文档标注与SDK实际校验逻辑不一致

## 问题原因

SDK会校验config和extraInfo参数，即使不配置也需要传空对象，文档未明确说明

## 解决方案

调用addTasks时，config和extraInfo即使不配置也要传空对象：config:{}, extraInfo:''

## 其他触发场景

（合并时在此处追加）
