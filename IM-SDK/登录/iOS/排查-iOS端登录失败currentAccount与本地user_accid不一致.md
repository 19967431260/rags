---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 登录
platform: iOS
title: iOS端登录失败currentAccount与本地user_accid不一致
root_cause: 用户在06:59时间点未成功发起登录请求,导致SDK未登录状态
solution: 需要获取SDK日志分析具体接口调用行为。建议联系用户重新登录并抓取日志进行详细排查。
customers: ["北京小刀万维"]
source: chat_history
tags: ["登录失败", "currentAccount", "iOS", "日志排查"]
created: 2026-02-04
updated: 2026-03-17
---

## 问题：iOS iOS端登录失败currentAccount与本地user_accid不一致

## 问题详情

**现象**：
iOS端用户(user_accid:1a26b3a5b67433174ecb4f5915180b0f,用户ID:6713120)在2026-02-04 06:59登录时,本地user_accid与SDK的currentAccount字段不一致,怀疑登录未成功。

## 排查过程

1. 检查服务器登录记录 → 06:59分服务器未收到登录请求
2. 查看用户登录时间线 → 上次离线2026-02-04 03:31:15.332,下次登录2026-02-04 08:15:23.037

**关键发现**:06:59时间点服务器无登录请求记录,用户实际未登录成功

## 问题原因

用户在06:59时间点未成功发起登录请求,导致SDK未登录状态

## 解决方案

需要获取SDK日志分析具体接口调用行为。建议联系用户重新登录并抓取日志进行详细排查。

## 其他触发场景

（暂无）
