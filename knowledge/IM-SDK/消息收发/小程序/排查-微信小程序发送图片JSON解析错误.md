---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息收发
platform: 小程序
title: 微信小程序发送图片必现失败JSON解析错误
root_cause: ""
solution: 需要提供可复现问题的最小demo进行调试排查，检查wannos-web.127.net域名是否被拦截，确认小程序web-view环境下的SDK集成配置是否正确。
customers: ["多抓鱼(北京)科技有限公司"]
source: chat_history
tags: ["小程序", "图片发送", "JSON解析", "web-view", "wannos-web.127.net"]
created: 2026-02-10
updated: 2026-03-16
---

## 问题：小程序 微信小程序发送图片必现失败JSON解析错误

## 问题详情

**现象**：
微信小程序环境下发送图片必现失败，文字消息可以正常发送，图片可以正常接收。错误日志显示JSON解析失败。必现。

**环境信息**：
- SDK版本：nim-web-sdk-ng 10.9.30
- UIKit版本：@xkit-yx/im-kit-ui 10.9.0
- 集成方式：小程序通过web-view组件引入云信Web SDK

**相关日志**：
JSON解析失败

## 排查过程

1. 检查错误日志 → JSON解析失败
2. 检查文字消息 → 正常发送
3. 检查图片接收 → 正常接收
4. 怀疑域名被拦截 → 检查https://wannos-web.127.net域名

**关键发现**：问题可能与域名拦截或小程序web-view环境有关，需要提供可复现demo进一步排查

## 问题原因

待进一步排查

## 解决方案

需要提供可复现问题的最小demo进行调试排查，检查wannos-web.127.net域名是否被拦截，确认小程序web-view环境下的SDK集成配置是否正确。

## 其他触发场景

