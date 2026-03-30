---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 登录
platform: Web
title: IM账号登录失败WebSocket连接断开
root_cause: 更换appkey后聊天室未重新创建成功
solution: 确保appkey与聊天室配置匹配；检查网络是否拦截WebSocket；监听deviceError和device-open-fail事件处理错误
customers: ["江苏华招网信息技术有限公司"]
source: chat_history
tags: ["登录", "WebSocket", "参数错误", "appkey", "聊天室"]
created: 2025-02-18
updated: 2026-03-20
---

## 问题：Web IM账号登录失败WebSocket连接断开

## 问题详情

**现象**：
IM账号登录不上，要么报超时要么报参数错误，WebSocket连上后马上就断。

## 排查过程

1. 查看日志发现WebSocket连接后立即断开
2. 建议检查用户网络是否把WebSocket拦截
3. 切换到无防火墙和VPN的手机4G/5G测试
4. 确认参数错误是连接重连失败后报的登录异常，不用关注
5. 最终自查发现是更换了appkey导致聊天室没创建成功

## 问题原因

更换appkey后聊天室未重新创建成功

## 解决方案

确保appkey与聊天室配置匹配；检查网络是否拦截WebSocket；监听deviceError和device-open-fail事件处理错误

## 其他触发场景
- [Web] IM账号登录失败WebSocket连接断开，来源：['江苏华招网信息技术有限公司']，2026-03-20
- [Web] IM账号登录失败WebSocket连接断开，来源：['江苏华招网信息技术有限公司']，2026-03-20

