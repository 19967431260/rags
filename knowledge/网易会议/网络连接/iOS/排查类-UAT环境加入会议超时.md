---
track_type: 排查类
sub_type: 线上事故
product: 网易会议
feature: 网络连接
platform: iOS
title: UAT环境加入会议超时
root_cause: UAT环境RTC QUIC协议端口(183.136.198.8:50171)网络不通，导致加入会议超时
solution: 开通UAT环境到RTC服务器UDP端口50171的网络访问策略
customers: ['宁波银行']
source: chat_history
tags: ['网易会议', 'UAT', '加入会议超时', 'QUIC', 'UDP', '50171', '网络策略']
created: 2025-01-13
updated: 2026-03-23
---

## 问题：UAT环境加入会议超时

## 问题详情

**现象**：
宁波银行UAT环境无法发起会议，选择参会人后停留在IM页面，或15秒后退出到IM页面，提示加入会议超时。

## 排查过程

1. 客户反馈UAT环境无法发起会议
2. 查看日志发现IM登录timeout错误
3. 怀疑TCP端口不通
4. 后端确认网络过期重新开通
5. 下午再次测试仍失败
6. 查看RTC日志发现quic握手超时
7. 确认RTC quic协议端口50171不通
8. 需要网络策略开通UDP端口

## 问题原因

UAT环境RTC QUIC协议端口(183.136.198.8:50171)网络不通，导致加入会议超时

## 解决方案

开通UAT环境到RTC服务器UDP端口50171的网络访问策略

## 其他触发场景

（合并时在此处追加）
