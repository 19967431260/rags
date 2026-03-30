---
track_type: 排查类
sub_type: 使用问题
product: 呼叫组件
feature: 被叫监听
platform: iOS
title: iOS端收不到onReceiveInvited被叫回调
root_cause: ""
solution: 检查Callkit组件是否正确初始化，确保日志已开启。提供appkey和收不到监听的用户accid，由技术支持拉取服务端日志定位问题。
customers: ["广州有爱中医门诊部有限公司"]
source: chat_history
tags: ["onReceiveInvited", "被叫回调", "iOS", "初始化"]
created: 2026-02-12
updated: 2026-03-16
---

## 问题：iOS iOS端收不到onReceiveInvited被叫回调

## 问题详情

**现象**：
iOS端能正常拨打呼叫，但别人呼叫过来时无法唤起被叫页面，onReceiveInvited回调未触发。必现。

## 排查过程

1. 检查日志 → Callkit组件日志未打开或未初始化
2. 提供测试账号拉取服务端日志排查

## 问题原因

待进一步排查

## 解决方案

检查Callkit组件是否正确初始化，确保日志已开启。提供appkey和收不到监听的用户accid，由技术支持拉取服务端日志定位问题。

## 其他触发场景

