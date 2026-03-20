---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 登录鉴权
platform: iOS
title: @麻世庆 我们云信域名改回link-hexin01
root_cause: 会话中表现为配置或接口使用不一致导致。
solution: @黄俐娴 不太建议的，link-sg.netease.im:7000是我们海外的通用域名，会比特定域名更稳定，泛化性更高一点。
customers: ["VIP云信—初晴/核芯"]
source: chat_history
tags: ["404", "500", "登录", "消息", "回调"]
created: 2024-12-31
updated: 2026-03-20
---

## 问题：iOS @麻世庆 我们云信域名改回link-hexin01

## 问题详情

@麻世庆 我们云信域名改回link-hexin01.netease.im:7003有什么影响吗？；这是一条引用/回复消息：；“麻世庆:；@周丹云  您好，根据对应的case来看，可能和原来的域名有关，咱们看下是否能让原来的link-hexin01.netease.im:7003域名调整到link-sg.netease.im:7000上，这个是海外的公有云域名，会比link-hexin01.netease.im:7003更稳定。”；------

## 排查过程

1. 根据会话记录核对配置与日志；2. 对关键接口与参数进行逐项验证。

## 问题原因

会话中表现为配置或接口使用不一致导致。

## 解决方案

@黄俐娴 不太建议的，link-sg.netease.im:7000是我们海外的通用域名，会比特定域名更稳定，泛化性更高一点。

## 其他触发场景
