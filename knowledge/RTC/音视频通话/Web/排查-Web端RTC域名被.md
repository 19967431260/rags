---
track_type: 排查类
sub_type: 客户环境问题
product: RTC
feature: 音视频通话
platform: Web
title: Web端RTC域名被防火墙拦截
root_cause: 交易中心防火墙将网易云信相关域名/IP误判为网易云音乐而拦截
solution: statistic.live.126.net为数据上报域名无法规避，建议客户向交易中心出具证明说明域名用途；yunxinvcloud.com可屏蔽，不影响会议功能
customers: ["金润方舟科技股份有限公司北京分公司"]
source: chat_history
tags: ["RTC", "Web", "域名拦截", "防火墙", "statistic.live.126.net"]
created: 2025-02-11
updated: 2026-03-20
---

## 问题：Web Web端RTC域名被防火墙拦截

## 问题详情

**现象**：
客户交易中心防火墙拦截了yunxinvcloud.com和statistic.live.126.net两个域名，导致无法正常进入音视频会议。statistic.live.126.net是数据上报域名，yunxinvcloud.com经测试屏蔽后一般不影响会议功能。

## 排查过程

1. 客户反馈交易中心屏蔽了yunxinvcloud.com和statistic.live.126.net两个域名
2. 确认statistic.live.126.net是RTC数据上报域名，无法规避
3. 测试发现yunxinvcloud.com屏蔽后不影响会议功能
4. 建议客户出具证明说明域名用途

## 问题原因

交易中心防火墙将网易云信相关域名/IP误判为网易云音乐而拦截

## 解决方案

statistic.live.126.net为数据上报域名无法规避，建议客户向交易中心出具证明说明域名用途；yunxinvcloud.com可屏蔽，不影响会议功能

## 其他触发场景
- [Web] Web端RTC域名被防火墙拦截，来源：['金润方舟科技股份有限公司北京分公司']，2026-03-20
- [Web] Web端RTC域名被防火墙拦截，来源：['金润方舟科技股份有限公司北京分公司']，2026-03-20

