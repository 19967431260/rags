---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 登录
platform: 微信小程序
title: 小程序token登录失败102302错误
root_cause: token生成与登录使用的appkey/accid不匹配，或域名配置不完整
solution: 1. 微信后台配置域名：https://lbs.netease.im
2. 代码初始化添加对应config
3. 调用服务端API重新设置token
customers: ["VIP云信-上海闲途科技有限公司"]
source: chat_history
tags: ["小程序", "登录", "102302", "token", "域名配置"]
created: 2025-02-20
updated: 2026-03-20
---

## 问题：微信小程序 小程序token登录失败102302错误

## 问题详情

**现象**：
小程序获取token后云信登录失败，返回102302错误码

## 排查过程

1. 确认域名配置 → 需在微信后台配置域名
2. 检查初始化配置 → 需添加lbs.netease.im域名
3. 确认错误原因 → appkey、accid、token三者不匹配

## 问题原因

token生成与登录使用的appkey/accid不匹配，或域名配置不完整

## 解决方案

1. 微信后台配置域名：https://lbs.netease.im
2. 代码初始化添加对应config
3. 调用服务端API重新设置token

## 其他触发场景

