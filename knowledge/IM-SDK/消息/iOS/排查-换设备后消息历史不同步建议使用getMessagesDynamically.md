---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息
platform: iOS
title: 换设备后消息历史不同步建议使用getMessagesDynamically
root_cause: 用户使用老版本9.1.1（三年半未更新），新设备登录后漫游消息同步时间戳不完整，导致消息历史未漫游下来。且用户没有主动调用fetchMessageHistory拉取云端历史消息。
solution: 1. 升级到最新版本（建议9.20.13或更高）\n2. 使用动态历史消息查询接口getMessagesDynamically（参考：https://doc.yunxin.163.com/messaging/guide/DYzOTY1NDc?platform=iOS）获取某个会话的完整历史消息，该方式比普通fetchMessageHistory更全面。
customers: ["杭州云汽配配科技有限公司"]
source: chat_history
tags: ["消息漫游","getMessagesDynamically","历史消息","换设备","iOS","同步"]
created: 2025-08-18
updated: 2026-03-26
---

## 问题：iOS 换设备后消息历史不同步建议使用getMessagesDynamically

## 问题详情

**现象**：
客户反映达人换设备登录后，与用户的私信历史记录不见了，客服查日志发现同步时间戳没有包含14号的消息。客服确认问题与旧版本（9.1.1，三年半未更新）有关。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客服拉取客户端日志分析 → 日志分析
2. 确认是同步时间戳问题 → 时间戳不完整
3. 发现旧版本9.1.1存在漫游消息同步缺陷 → 版本问题
4. 新设备登录后没有调用fetchMessageHistory获取历史消息 → 调用缺失

**关键发现**：用户使用老版本9.1.1（三年半未更新），新设备登录后漫游消息同步时间戳不完整，导致消息历史未漫游下来。且用户没有主动调用fetchMessageHistory拉取云端历史消息。

## 问题原因

用户使用老版本9.1.1（三年半未更新），新设备登录后漫游消息同步时间戳不完整，导致消息历史未漫游下来。且用户没有主动调用fetchMessageHistory拉取云端历史消息。

## 解决方案

1. 升级到最新版本（建议9.20.13或更高）
2. 使用动态历史消息查询接口getMessagesDynamically（参考：https://doc.yunxin.163.com/messaging/guide/DYzOTY1NDc?platform=iOS）获取某个会话的完整历史消息，该方式比普通fetchMessageHistory更全面。

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
