---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 音视频通话
platform: 微信小程序
title: 微信小程序control消息接收方收不到
root_cause: 可能还是监听时机或方式问题，需要进一步分析
solution: 建议提供最小化复现问题的demo项目，让研发本地运行调试分析
customers: ['FVIP云信-智业互联健康科技']
source: chat_history
tags: ['微信小程序', 'control', 'clientLeave', '监听', '音视频通话']
created: 2025-01-06
updated: 2026-03-23
---

## 问题：微信小程序 微信小程序control消息接收方收不到

## 问题详情

**现象**：
微信小程序发送netcall.control命令后，接收方经常性接收不到，clientLeave事件也基本没收到过。

**环境信息**：
- 平台：微信小程序
- 产品：RTC

## 排查过程

1. 确认监听时机：初始化之后、通话发起之前已监听\n2. 检查其他事件(clientJoin)是否正常\n3. 要求提供最小化复现demo\n4. 研发本地调试分析

## 问题原因

可能还是监听时机或方式问题，需要进一步分析

## 解决方案

建议提供最小化复现问题的demo项目，让研发本地运行调试分析

## 其他触发场景

（合并时在此处追加）
