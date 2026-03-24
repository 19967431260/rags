---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 登录鉴权
platform: Uniapp
title: 403错误-动态token登录配置不匹配
root_cause: 管理后台配置了动态token登录，但客户端仍使用静态token方式登录，导致鉴权失败。
solution: 修改客户端登录接口nim.V2NIMLoginService.login的参数，使用动态token登录方式（传入正确的authtype和token）。
customers: ['北京新流通信息科技有限公司']
source: chat_history
tags: ['403', '动态token', '登录失败', '鉴权']
created: 2025-01-10
updated: 2026-03-23
---

## 问题：Uniapp 403错误-动态token登录配置不匹配

## 问题详情

**现象**：
客户使用动态token登录时返回403错误。

## 排查过程

1. 检查管理后台配置，发现勾选了动态token登录；2. 检查客户端登录方式，发现使用静态token方式登录；3. 确认需要修改客户端登录接口参数。

## 问题原因

管理后台配置了动态token登录，但客户端仍使用静态token方式登录，导致鉴权失败。

## 解决方案

修改客户端登录接口nim.V2NIMLoginService.login的参数，使用动态token登录方式（传入正确的authtype和token）。

## 其他触发场景

（合并时在此处追加）
