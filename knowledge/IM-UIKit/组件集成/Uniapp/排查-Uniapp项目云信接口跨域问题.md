---
track_type: 排查类
sub_type: 集成类
product: IM-UIKit
feature: 组件集成
platform: Uniapp
title: Uniapp项目云信接口跨域问题
root_cause: 项目中的请求拦截器在header中添加了自定义platform参数，导致云信接口跨域
solution: 移除或过滤掉云信域名的自定义header参数（如platform），避免影响云信接口请求
customers: ['VIP云信-云南国云药材国际交易有限公司']
source: chat_history
tags: ['UIKit', 'Uniapp', '跨域', 'header', 'platform']
created: 2025-02-20
updated: 2026-03-23
---

## 问题：Uniapp Uniapp项目云信接口跨域问题

## 问题详情

**现象**：
自己的Uniapp项目调用云信接口出现跨域错误，但官方Demo没有跨域问题

**环境信息**：
- 平台：Uniapp
- 产品：IM-UIKit

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 检查项目代理配置
2. 对比Demo和项目差异
**关键发现**：项目中header添加了自定义platform参数导致跨域

## 问题原因

项目中的请求拦截器在header中添加了自定义platform参数，导致云信接口跨域

## 解决方案

移除或过滤掉云信域名的自定义header参数（如platform），避免影响云信接口请求

## 其他触发场景

（合并时在此处追加：`- [Uniapp] Uniapp项目云信接口跨域问题，来源：['VIP云信-云南国云药材国际交易有限公司']，2026-03-23`）
