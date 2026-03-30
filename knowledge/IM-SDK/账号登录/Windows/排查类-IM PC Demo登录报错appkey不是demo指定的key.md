---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 账号登录
platform: Windows
title: IM PC Demo登录报错appkey不是demo指定的key
root_cause: demo包含MD5 token加密逻辑，与正式环境不兼容
solution: 全局搜索并注释MD5相关代码，调用服务器API创建账号
customers: ['广州群市网络科技有限公司']
source: chat_history
tags: ['IM V9', 'Windows', 'demo', '登录', 'appkey', 'MD5']
created: 2025-01-16
updated: 2026-03-23
---

## 问题：IM PC Demo登录报错appkey不是demo指定的key

## 问题详情

**现象**：
客户使用IM PC Demo修改appkey后登录报错，且登录提示账号密码错误。

## 排查过程

1. 客户反馈demo注册接口报错
2. 告知demo注册接口不可用
3. 客户修改appkey后登录报302错误
4. 检查发现demo有MD5 token加密逻辑

## 问题原因

demo包含MD5 token加密逻辑，与正式环境不兼容

## 解决方案

全局搜索并注释MD5相关代码，调用服务器API创建账号

## 其他触发场景

（合并时在此处追加）
