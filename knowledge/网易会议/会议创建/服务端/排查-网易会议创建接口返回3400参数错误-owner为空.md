---
track_type: 排查类
sub_type: 集成类
product: 网易会议
feature: 会议创建
platform: 服务端
title: 网易会议创建接口返回3400参数错误-owner为空
root_cause: 创建会议接口缺少必传参数owner（会议所有者/创建者ID）。
solution: 创建会议接口需要传入owner字段，值为会议所有者的用户ID。
customers: ["杭州数垚科技有限公司"]
source: chat_history
tags: ["3400", "参数错误", "owner", "创建会议", "roomkit"]
created: 2025-05-16
updated: 2025-03-20
---

## 问题：服务端 网易会议创建接口返回3400参数错误-owner为空

## 问题详情

**现象**：
调用网易会议创建接口返回code:3400，msg:参数错误。请求参数包含subject、startTime、endTime、roomConfig等字段。

**环境信息**：
- SDK 版本：
- 系统版本 / 设备：
- 平台：服务端

## 排查过程

1. 客户调用创建会议接口返回参数错误 → 技术支持排查发现未传owner字段
2. 客户移除scheduleUid后仍报错 → 技术支持确认需要传owner参数
3. 补充owner参数后创建成功

## 问题原因

创建会议接口缺少必传参数owner（会议所有者/创建者ID）。

## 解决方案

创建会议接口需要传入owner字段，值为会议所有者的用户ID。

## 其他触发场景

