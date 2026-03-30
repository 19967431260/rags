---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 登录连接
platform: HarmonyOS
title: 鸿蒙端私有化环境登录connect fail错误192001
root_cause: 鸿蒙端使用wss通道通信，需要使用webconf.jsp配置而非其他端使用的conf配置
solution: 私有化环境鸿蒙端初始化时，lbs和link配置应使用webconf.jsp（或jwebconf.jsp）而非conf配置，因为鸿蒙走的是wss通道
customers: []
source: chat_history
tags: []
created: 2025-02-01
updated: 2025-03-20
---

# 鸿蒙端私有化环境登录connect fail错误192001

## 问题描述

鸿蒙OS端在私有化环境进行login时提示connect fail，错误码192001(V2NIM_ERROR_CODE_CONNECT_FAILED)，其他端正常，lbs配置可正常访问

## 问题背景

1. 查看日志发现错误码192001，确认是连接错误
2. 确认私有化环境配置正确，其他端正常
3. 排查发现鸿蒙端配置方式与其他端不同

**关键发现**：鸿蒙走的是wss通道，需要使用web端配置

## 根因分析

鸿蒙端使用wss通道通信，需要使用webconf.jsp配置而非其他端使用的conf配置

## 解决方案

私有化环境鸿蒙端初始化时，lbs和link配置应使用webconf.jsp（或jwebconf.jsp）而非conf配置，因为鸿蒙走的是wss通道

## 标签

- 192001
- connect fail
- 鸿蒙
- HarmonyOS
- 私有化
- webconf.jsp
- wss

## 客户

- 星网锐捷

## 会话日期

2025-02-10
