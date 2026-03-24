---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息收发
platform: 服务端
title: IM content消息乱码显示问号
root_cause: 服务端请求时编码格式问题
solution: 检查服务端请求时的赋值情况，确保编码格式正确
customers: ["点点云智能科技有限公司"]
source: chat_history
tags: ["乱码", "编码", "content", "服务端API", "???"]
created: 2025-02-25
updated: 2026-03-20
---

## 问题：服务端 IM content消息乱码显示问号

## 问题详情

**现象**：
IM content消息乱码，监听到???这种，除了123其他都是????。

## 排查过程

1. 询问消息ID → 客户提供的是用户ID
2. 确认是服务端API发的系统通知
3. 查看服务端请求时的赋值情况
4. 发现是编码问题

## 问题原因

服务端请求时编码格式问题

## 解决方案

检查服务端请求时的赋值情况，确保编码格式正确

## 其他触发场景
- [服务端] IM content消息乱码显示问号，来源：['点点云智能科技有限公司']，2026-03-20

