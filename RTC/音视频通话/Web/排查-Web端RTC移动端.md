---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 音视频通话
platform: Web
title: Web端RTC移动端初始化报错OverConstrainedError
root_cause: 指定的采集参数无法被任何可用设备满足，一般是由于采集设备被占用、设备名填错或者不支持指定的分辨率
solution: 检查采集设备是否被占用，确认设备名称正确，调整分辨率参数至设备支持的范围，会触发deviceError回调
customers: ["金润方舟科技股份有限公司北京分公司"]
source: chat_history
tags: ["RTC", "Web", "移动端", "OverConstrainedError", "本地流初始化"]
created: 2025-02-17
updated: 2026-03-20
---

## 问题：Web Web端RTC移动端初始化报错OverConstrainedError

## 问题详情

**现象**：
在移动端环境（手机浏览器、PC开发工具模拟移动端）初始化本地流时报错OverConstrainedError，提示采集参数无法满足。

## 排查过程

1. 客户反馈手机浏览器和PC开发工具模拟移动端都报错
2. 查看日志发现OverConstrainedError错误
3. 分析为采集参数无法被设备满足

## 问题原因

指定的采集参数无法被任何可用设备满足，一般是由于采集设备被占用、设备名填错或者不支持指定的分辨率

## 解决方案

检查采集设备是否被占用，确认设备名称正确，调整分辨率参数至设备支持的范围，会触发deviceError回调

## 其他触发场景
- [Web] Web端RTC移动端初始化报错OverConstrainedError，来源：['金润方舟科技股份有限公司北京分公司']，2026-03-20
- [Web] Web端RTC移动端初始化报错OverConstrainedError，来源：['金润方舟科技股份有限公司北京分公司']，2026-03-20

