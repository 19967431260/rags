---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 登录
platform: Uniapp
title: Uniapp小程序动态token登录失败
root_cause: 小程序环境配置与dev环境不对应，导致生成的token无法通过校验
solution: V9版本不需要使用tokenProvider，直接设置token字段即可；确保域名和环境配置对应
customers: ["南京芷间科技有限公司"]
source: chat_history
tags: ["动态token", "登录失败", "Uniapp", "小程序", "tokenProvider"]
created: 2025-02-12
updated: 2026-03-20
---

## 问题：Uniapp Uniapp小程序动态token登录失败

## 问题详情

**现象**：
Uniapp小程序端使用动态token登录失败，提示用户名或密码不正确。同样账号在PC端获取token后可用，小程序端不可用。

## 排查过程

1. 检查token生成逻辑 → 发现base64前的json中多了一个timestamp字段
2. 检查token参数 → 发现tokenProvider写法是V10版本，而客户使用的是V9
3. 检查服务端token校验 → 确认token校验逻辑正常
4. 检查appkey配置 → 最终发现是环境配置问题导致token不匹配

## 问题原因

小程序环境配置与dev环境不对应，导致生成的token无法通过校验

## 解决方案

V9版本不需要使用tokenProvider，直接设置token字段即可；确保域名和环境配置对应

## 其他触发场景
- [Uniapp] Uniapp小程序动态token登录失败，来源：['南京芷间科技有限公司']，2026-03-20
- [Uniapp] Uniapp小程序动态token登录失败，来源：['南京芷间科技有限公司']，2026-03-20

