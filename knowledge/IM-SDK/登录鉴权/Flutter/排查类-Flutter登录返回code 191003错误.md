---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 登录鉴权
platform: Flutter
title: Flutter登录返回code 191003错误
root_cause: 客户使用静态token注册账号，但登录策略设置为动态token登录（authType=1），导致鉴权失败。
solution: 将鉴权方式改为0（静态token登录），一般使用静态token登录即可满足需求。
customers: ['武汉极意网络科技有限公司']
source: chat_history
tags: ['191003', 'Flutter', '登录失败', '鉴权', '静态token', '动态token']
created: 2025-01-16
updated: 2026-03-23
---

## 问题：Flutter登录返回code 191003错误

## 问题详情

**现象**：
Flutter客户端初始化SDK成功返回code 0，但调用登录接口返回code:191003。客户使用服务端API注册账号，但登录时鉴权方式设置为1（动态token），而实际使用的是静态token。

## 排查过程

1. 检查账号注册情况 → 发现账号122已注册存在\n2. 确认登录方式 → 客户使用静态token注册但鉴权方式设置为1\n3. 建议修改鉴权方式 → 改为0（静态token登录）

## 问题原因

客户使用静态token注册账号，但登录策略设置为动态token登录（authType=1），导致鉴权失败。

## 解决方案

将鉴权方式改为0（静态token登录），一般使用静态token登录即可满足需求。

## 其他触发场景

（合并时在此处追加）
