---
track_type: 咨询类
sub_type: 能力与边界咨询
product: RTC
feature: 计费规则
platform: 通用
title: RTC计费开始节点说明
root_cause: 
solution: RTC计费按时长计算，从用户join进channel后开始计时。IM计费按日活计算，客户端login时算一次日活。SDK初始化和获取token不计费，只有实际使用服务器流量（join频道）才开始计费。
customers: ['江苏福美裕医疗科技有限公司']
source: chat_history
tags: ['RTC', '计费', '计费节点', 'join', '时长计费']
created: 2025-01-22
updated: 2026-03-23
---

## 问题：RTC计费开始节点说明

## 问题详情

**现象**：
客户咨询产品收费开始的节点，是从请求getToken接口响应开始还是其他节点。

## 排查过程



## 问题原因



## 解决方案

RTC计费按时长计算，从用户join进channel后开始计时。IM计费按日活计算，客户端login时算一次日活。SDK初始化和获取token不计费，只有实际使用服务器流量（join频道）才开始计费。

## 其他触发场景

（合并时在此处追加）
