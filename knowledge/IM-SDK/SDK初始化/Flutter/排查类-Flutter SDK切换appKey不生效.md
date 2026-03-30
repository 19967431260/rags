---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: SDK初始化
platform: Flutter
title: Flutter SDK切换appKey不生效
root_cause: Flutter SDK不支持在不重启APP的情况下切换appKey，原生SDK支持在登录接口设置appKey但Flutter层未封装该功能。
solution: 切换环境（需要更换appKey）时需要重启APP，Flutter SDK暂不支持动态切换appKey。
customers: ['武汉乐乐助推科技有限公司']
source: chat_history
tags: ['Flutter', 'appKey', '初始化', '切换环境', '302', 'pwdError']
created: 2025-01-14
updated: 2026-03-23
---

## 问题：Flutter SDK切换appKey不生效

## 问题详情

**现象**：
客户反馈在不重启APP的情况下重新初始化SDK，设置新的appKey不会生效，导致登录失败（302错误）。

## 排查过程

1. 客户反馈同一账号在一台手机可登录，另一台无法登录
2. 错误提示为pwdError（密码错误）
3. 客户发现切环境后初始化SDK，appKey没有生效
4. 技术支持确认Flutter不支持在登录接口中设置appKey
5. 建议切环境后重启APP

## 问题原因

Flutter SDK不支持在不重启APP的情况下切换appKey，原生SDK支持在登录接口设置appKey但Flutter层未封装该功能。

## 解决方案

切换环境（需要更换appKey）时需要重启APP，Flutter SDK暂不支持动态切换appKey。

## 其他触发场景

（合并时在此处追加）
