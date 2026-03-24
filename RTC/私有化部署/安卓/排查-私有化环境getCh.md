---
track_type: 排查类
sub_type: 集成类
product: RTC
feature: 私有化部署
platform: 安卓
title: 私有化环境getChannelInfos接口500错误排查
root_cause: 私有化环境部署问题，可能涉及服务未启动或网络不通
solution: 检查服务状态，确认所有容器正常运行，验证网络连通性
customers: ["杭州诚道道路交通研究院"]
source: chat_history
tags: ["RTC", "私有化", "getChannelInfos", "500错误", "安卓"]
created: 2025-02-19
updated: 2026-03-20
---

## 问题：安卓 私有化环境getChannelInfos接口500错误排查

## 问题详情

**现象**：
私有化部署环境下，安卓客户端调用getChannelInfos接口返回500错误，服务端日志显示请求未到达。

## 排查过程

1. 客户端日志搜索get channel info关键词
2. 检查服务端容器状态：docker ps -a | grep -i unheal
3. 检查nginx是否收到请求
4. 检查nertc-gateway转发日志
5. 确认客户端网络能访问服务端地址

## 问题原因

私有化环境部署问题，可能涉及服务未启动或网络不通

## 解决方案

检查服务状态，确认所有容器正常运行，验证网络连通性

## 其他触发场景
- [安卓] 私有化环境getChannelInfos接口500错误排查，来源：['杭州诚道道路交通研究院']，2026-03-20
- [安卓] 私有化环境getChannelInfos接口500错误排查，来源：['杭州诚道道路交通研究院']，2026-03-20

