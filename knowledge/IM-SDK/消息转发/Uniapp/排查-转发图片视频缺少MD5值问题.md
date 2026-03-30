---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息转发
platform: Uniapp
title: 转发图片视频缺少MD5值问题
root_cause: Uniapp非浏览器平台没有file对象，原始消息发送时就没有md5值
solution: 服务端API转发时随机生成一个md5值绕过字段校验；后续版本会优化去掉校验或SDK随机补md5
customers: ['VIP云信-元储文化科技（海南）有限公司']
source: chat_history
tags: ['转发', 'MD5', 'Uniapp', '图片', '视频']
created: 2025-02-07
updated: 2026-03-23
---

## 问题：Uniapp 转发图片视频缺少MD5值问题

## 问题详情

**现象**：
客户反馈转发图片或视频时提示需要文件的MD5值，但转发文件消息自带MD5，图片视频没有

**环境信息**：
- 平台：Uniapp
- 产品：IM-SDK

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客户提供发送代码截图
2. 检查发现原始消息是Web端发送
**关键发现**：Uniapp非浏览器平台没有file对象拿不到md5值，Web端发送的图片视频缺少md5

## 问题原因

Uniapp非浏览器平台没有file对象，原始消息发送时就没有md5值

## 解决方案

服务端API转发时随机生成一个md5值绕过字段校验；后续版本会优化去掉校验或SDK随机补md5

## 其他触发场景

（合并时在此处追加：`- [Uniapp] 转发图片视频缺少MD5值问题，来源：['VIP云信-元储文化科技（海南）有限公司']，2026-03-23`）
