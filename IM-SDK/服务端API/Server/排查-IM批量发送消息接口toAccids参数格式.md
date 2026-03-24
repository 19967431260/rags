---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 服务端API
platform: Server
title: IM批量发送消息接口toAccids参数格式
root_cause: 请求体封装格式问题
solution: 使用curl测试正确格式：curl -X POST -H "AppKey: xxx" -H "Nonce: xxx" -H "CurTime: xxx" -H "CheckSum: xxx" -H "Content-Type: application/x-www-form-urlencoded" -d 'fromAccid=zhangsan&toAccids=["aaa","bbb"]&type=0&body={"msg":"hello"}' 'https://api.netease.im/nimserver/msg/sendBatchMsg.action'
customers: ['VIP云信-邯郸市趣网传媒技术有限公司']
source: chat_history
tags: ['sendBatchMsg', 'toAccids', '批量发送', 'API']
created: 2025-01-17
updated: 2026-03-23
---

## 问题：Server IM批量发送消息接口toAccids参数格式

## 问题详情

**现象**：
批量发送消息时返回错误，提示toAccids参数不对。使用V9 API发送批量消息

## 排查过程



## 问题原因

请求体封装格式问题

## 解决方案

使用curl测试正确格式：curl -X POST -H "AppKey: xxx" -H "Nonce: xxx" -H "CurTime: xxx" -H "CheckSum: xxx" -H "Content-Type: application/x-www-form-urlencoded" -d 'fromAccid=zhangsan&toAccids=["aaa","bbb"]&type=0&body={"msg":"hello"}' 'https://api.netease.im/nimserver/msg/sendBatchMsg.action'

## 其他触发场景

（合并时在此处追加）
