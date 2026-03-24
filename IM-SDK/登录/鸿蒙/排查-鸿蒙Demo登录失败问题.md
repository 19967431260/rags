---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 登录
platform: 鸿蒙
title: 鸿蒙Demo登录失败问题
root_cause: 1. 鸿蒙使用了MD5加密，需要在demo中去掉MD5加密
2. 包名校验未关闭
solution: 1. 鸿蒙SDK使用MD5加密，在API demo中需要去掉MD5加密逻辑
2. 关闭包名校验后即可正常登录测试
customers: []
source: chat_history
tags: []
created: 2025-02-01
updated: 2025-03-20
---

# 鸿蒙Demo登录失败问题

## 问题描述

客户使用鸿蒙Demo测试时登录失败，提示APPKEY不存在

## 问题背景

- 检查token加密方式和包名校验

## 根因分析

1. 鸿蒙使用了MD5加密，需要在demo中去掉MD5加密
2. 包名校验未关闭

## 解决方案

1. 鸿蒙SDK使用MD5加密，在API demo中需要去掉MD5加密逻辑
2. 关闭包名校验后即可正常登录测试

## 标签

- 鸿蒙
- 登录
- MD5加密
- 包名校验
- Demo

## 客户

- FVIP云信-湖南惠农

## 会话日期

2025-02-20
