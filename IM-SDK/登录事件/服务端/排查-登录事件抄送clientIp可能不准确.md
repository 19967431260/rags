---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 登录事件
platform: 服务端
title: 登录事件抄送clientIp可能不准确：用户使用VPN导致IP归属异常
root_cause: 用户使用VPN导致IP归属与实际地理位置不符；SDK通过系统上报IP，该IP经过VPN转发后归属地与真实位置不符
solution: 抄送的clientIp是SDK通过系统上报获取的；如需验证可让用户访问whatismyip等页面确认实际IP；部分用户使用VPN导致IP归属地与实际不符属正常现象
customers: ["罗克佳华"]
source: chat_history
tags: ["clientIp", "VPN", "IP归属", "登录事件抄送"]
created: 2025-07-04
updated: 2025-07-25
---

## 问题：登录事件抄送clientIp可能不准确：用户使用VPN导致IP归属异常

## 问题原因

用户使用VPN导致IP归属与实际地理位置不符；SDK通过系统上报IP，该IP经过VPN转发后归属地与真实位置不符

## 解决方案

抄送的clientIp是SDK通过系统上报获取的；如需验证可让用户访问whatismyip等页面确认实际IP；部分用户使用VPN导致IP归属地与实际不符属正常现象
