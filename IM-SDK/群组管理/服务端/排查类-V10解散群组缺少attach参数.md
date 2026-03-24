---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 群组管理
platform: 服务端
title: V10解散群组缺少attach参数
root_cause: 客户封装的接口方法可能缺少attach参数导致调用失败。
solution: 解散群组接口需要确保参数格式正确，包含必要的attach字段。
customers: ['杭州白豪斯出海商业管理有限公司']
source: chat_history
tags: ['IM V10', '解散群组', 'attach', '参数错误']
created: 2025-01-15
updated: 2026-03-23
---

## 问题：V10解散群组缺少attach参数

## 问题详情

**现象**：
客户反馈V10解散群组接口返回null，请求参数与文档一致但调用失败。

## 排查过程

1. 客户反馈解散群组返回null
2. 技术支持怀疑有非json格式参数
3. 客户尝试添加attach参数后请求成功
4. 技术支持测试确认body参数可以正常调用

## 问题原因

客户封装的接口方法可能缺少attach参数导致调用失败。

## 解决方案

解散群组接口需要确保参数格式正确，包含必要的attach字段。

## 其他触发场景

（合并时在此处追加）
