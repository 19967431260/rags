---
track_type: 排查类
sub_type: 客户环境问题
product: RTC
feature: 基础功能
platform: Server
title: SpringBoot框架音频回调崩溃
root_cause: "SpringBoot框架与SDK兼容性问题"
solution: "逐步排除法，从最小代码开始添加模块"
customers: ["云信"]
source: chat_history
tags: ["token","消息"]
created: 2025-06-20
updated: 2025-03-23
---

## 问题：SpringBoot框架音频回调崩溃

## 问题详情

**现象**：
使用纯java工程调用不会崩溃，引入springboot框架后音频回调必崩溃。

**环境信息**：
- 平台：Server
- 框架：SpringBoot
- 系统：CentOS

## 排查过程

1. 对比测试 → 纯java工程正常，SpringBoot崩溃
2. 初步排查 → 不是云信SDK本身代码问题，结合飞虎库后崩溃
3. 建议方案 → 逐步过滤排除

## 问题原因

初查不是云信SDK本身代码的问题，但是结合飞虎的库之后就崩了。

## 解决方案

逐步过滤排除：
1. 先写一个关联模块最少的代码开始
2. hard code写serverAddress settings
3. appkey token cname uid也先用hard code方式写进去
4. 用这个方式先跑起来（这个方式audioframeobserver不会崩）
5. 跑起来之后再慢慢加相关联的模块，看看哪个模块有影响

## 其他触发场景

