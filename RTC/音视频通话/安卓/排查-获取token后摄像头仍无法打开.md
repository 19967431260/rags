---
track_type: 排查类
sub_type: 集成类
product: RTC
feature: 音视频通话
platform: 安卓
title: 获取token后摄像头仍无法打开
root_cause: 本地自行拼接token参数可能不正确，建议使用官方示例代码生成token。
solution: 使用官方提供的token生成示例代码：https://github.com/netease-im/G2-API-Examples/tree/main/server/token_server/java，按照示例参数和算法生成token。
customers: ['云信-国信网安（上海）大数据科技']
source: chat_history
tags: ['RTC', 'token', '摄像头', 'Android', '鉴权']
created: 2025-02-21
updated: 2026-03-23
---

## 问题：安卓 获取token后摄像头仍无法打开

## 问题详情

**现象**：
按照教程在Android demo中获取token后，摄像头仍然无法打开。

**环境信息**：
- 平台：安卓
- 产品：RTC

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 确认token已生成
2. 检查token获取方式
3. 发现使用本地自行拼接token
4. 后台查询鉴权失败

## 问题原因

本地自行拼接token参数可能不正确，建议使用官方示例代码生成token。

## 解决方案

使用官方提供的token生成示例代码：https://github.com/netease-im/G2-API-Examples/tree/main/server/token_server/java，按照示例参数和算法生成token。

## 其他触发场景

（合并时在此处追加：`- [安卓] 获取token后摄像头仍无法打开，来源：['云信-国信网安（上海）大数据科技']，2026-03-23`）
