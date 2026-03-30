---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 云端录制
platform: 服务端
title: 云端录制指定UID单流录制配置方法
root_cause: 1. 客户端同时开启了录制导致冲突；2. 使用streamSubscribe指定UID时，需要同时设置streamType参数。
solution: 1. 注释掉客户端录制代码；2. 调用录制接口时设置streamSubscribe参数，指定audioUidList和videoUidList，并设置streamType为2。
customers: ['临沂卓创网络科技有限公司']
source: chat_history
tags: ['RTC', '云端录制', '单流录制', 'streamSubscribe', 'recordType']
created: 2025-02-11
updated: 2026-03-23
---

## 问题：服务端 云端录制指定UID单流录制配置方法

## 问题详情

**现象**：
客户需要只录制指定UID的音视频流，但配置后仍生成多个视频文件（包含合流和单流），需要了解正确的参数配置。

**环境信息**：
- 平台：服务端
- 产品：RTC

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客户配置layoutConfig和recordConfig → 仍生成3个视频
2. 添加recordType:2参数 → 仍生成2个视频
3. 检查客户端代码 → 发现安卓端同时开启了客户端录制，与服务端录制冲突
4. 注释安卓端录制代码后，只传cid测试 → 可以正常录制
5. 添加streamSubscribe参数指定UID → 报错414 streamSubscribe.streamType
6. 添加streamType:2参数 → 成功只录制指定UID

## 问题原因

1. 客户端同时开启了录制导致冲突；2. 使用streamSubscribe指定UID时，需要同时设置streamType参数。

## 解决方案

1. 注释掉客户端录制代码；2. 调用录制接口时设置streamSubscribe参数，指定audioUidList和videoUidList，并设置streamType为2。

## 其他触发场景

（合并时在此处追加：`- [服务端] 云端录制指定UID单流录制配置方法，来源：['临沂卓创网络科技有限公司']，2026-03-23`）
