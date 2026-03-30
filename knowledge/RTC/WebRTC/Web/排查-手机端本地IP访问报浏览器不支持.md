---
track_type: 排查类
sub_type: 集成类
product: RTC
feature: WebRTC
platform: Web
title: 手机端本地IP访问报浏览器不支持
root_cause: WebRTC要求使用https或localhost地址,本地IP地址不符合安全要求
solution: 部署到https环境或使用localhost地址访问
customers: ["杭州帆特科技有限公司"]
source: chat_history
tags: ["WebRTC","https","localhost","浏览器支持","手机端"]
created: 2026-02-04
updated: 2026-03-17
---

## 问题：Web 手机端本地IP访问报浏览器不支持

## 问题详情

**现象**：
NERTC.checkSystemRequirements()返回true,但手机端使用本地IP地址(非localhost)访问时报浏览器不支持错误

## 排查过程

1. 调用NERTC.checkSystemRequirements() → 返回true
2. 手机端使用本地IP地址访问 → 报浏览器不支持

**关键发现**: 使用的是本地IP而非https或localhost

## 问题原因

WebRTC要求使用https或localhost地址,本地IP地址不符合安全要求

## 解决方案

部署到https环境或使用localhost地址访问

## 其他触发场景

