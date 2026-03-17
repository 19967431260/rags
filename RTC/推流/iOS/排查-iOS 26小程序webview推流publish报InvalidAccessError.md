---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 推流
platform: iOS
title: iOS 26小程序webview推流publish报InvalidAccessError
root_cause: webview环境userAgent被串改，SDK无法有效判断当前手机系统版本是iOS 26+。
solution: 在join()之前调用NERTC.getParameters().enableCompatibleWithIOS26 = true。业务层判断系统是iOS 26+时设置此参数，如无法判断可直接设置。
customers: ["银河视界"]
source: chat_history
tags: ["iOS26","InvalidAccessError","publish","webview","userAgent"]
created: 2026-02-04
updated: 2026-03-17
---

## 问题：iOS iOS 26小程序webview推流publish报InvalidAccessError

## 问题详情

**现象**：
iOS 26系统在小程序webview中使用RTC推流时报错：[NERTC:ERROR:0170] publish() 内部错误: InvalidAccessError - Failed to set remote answer sdp: Failed to set recv parameters for m-section with mid='0'。自己能看到自己，但别人看不到推流。

## 排查过程

1. 检查userAgent → 发现webview环境userAgent被串改为iOS 18_7
2. 分析系统版本 → 实际系统是iOS 26
3. 定位问题 → SDK无法通过userAgent正确判断系统版本

**关键发现**：webview环境userAgent与实际系统版本不匹配导致SDK兼容性处理失效

## 问题原因

webview环境userAgent被串改，SDK无法有效判断当前手机系统版本是iOS 26+。

## 解决方案

在join()之前调用NERTC.getParameters().enableCompatibleWithIOS26 = true。业务层判断系统是iOS 26+时设置此参数，如无法判断可直接设置。

## 其他触发场景

