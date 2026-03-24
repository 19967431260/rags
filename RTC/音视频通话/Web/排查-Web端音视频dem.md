---
track_type: 排查类
sub_type: 集成类
product: RTC
feature: 音视频通话
platform: Web
title: Web端音视频demo获取token报错
root_cause: 未在demo中配置AppSecret导致token计算失败
solution: 在控制台获取AppSecret并配置到demo中。注意：正式开发时AppSecret只能在业务服务器使用，不能写到前端代码中
customers: ["VIP云信-广州市曜辰科技有限公司"]
source: chat_history
tags: ["RTC", "Web", "token", "AppSecret", "demo"]
created: 2025-02-17
updated: 2026-03-20
---

## 问题：Web Web端音视频demo获取token报错

## 问题详情

**现象**：
Web端运行音视频demo时获取token失败，报错信息提示缺少必要参数。

## 排查过程

1. 检查common/index.js中getToken是否有结果
2. 发现未配置AppSecret
3. 配置AppSecret后问题解决

## 问题原因

未在demo中配置AppSecret导致token计算失败

## 解决方案

在控制台获取AppSecret并配置到demo中。注意：正式开发时AppSecret只能在业务服务器使用，不能写到前端代码中

## 其他触发场景
- [Web] Web端音视频demo获取token报错，来源：['VIP云信-广州市曜辰科技有限公司']，2026-03-20
- [Web] Web端音视频demo获取token报错，来源：['VIP云信-广州市曜辰科技有限公司']，2026-03-20

