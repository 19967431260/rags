---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 群成员管理
platform: 服务端
title: 移除群成员接口返回team_id is required
root_cause: 接口需要表单提交（application/x-www-form-urlencoded），而非JSON格式
solution: 使用表单格式提交请求（application/x-www-form-urlencoded），踢人出群和主动退群的参数都放在query中。踢人出群时成员列表传string数组格式：["aaa","bbb"]。
customers: ['Eagle']
source: chat_history
tags: ['服务端', '移除成员', 'team_id', '414', '表单提交', 'query参数']
created: 2025-01-14
updated: 2026-03-23
---

## 问题：服务端 移除群成员接口返回team_id is required

## 问题详情

**现象**：
调用移除群成员接口时返回{"code":414,"msg":"team_id is required","data":{}}。

## 排查过程

1. 客户反馈接口报错 → 技术支持检查发现team_id未传或类型不对 → 建议用第三方工具测试 → 客户用postman测试同样报错 → 技术支持确认请求方式 → 发现Content-Type应为表单提交

## 问题原因

接口需要表单提交（application/x-www-form-urlencoded），而非JSON格式

## 解决方案

使用表单格式提交请求（application/x-www-form-urlencoded），踢人出群和主动退群的参数都放在query中。踢人出群时成员列表传string数组格式：["aaa","bbb"]。

## 其他触发场景

（合并时在此处追加）
