---
track_type: 排查类
sub_type: 集成类
product: RTC
feature: 音视频通话
platform: 安卓
title: RTC Demo摄像头黑屏问题
root_cause: appkey设置为安全模式，加入房间需要传入token鉴权，Demo默认未配置token。
solution: 1. 按照文档获取token：https://doc.yunxin.163.com/nertc/server-apis/TcxNDAxMTI?platform=server
2. 加入房间时传入token参数
3. 或临时将管理后台鉴权模式调整为非安全模式（上线仍需使用token鉴权）。
customers: ['云信-国信网安（上海）大数据科技']
source: chat_history
tags: ['RTC', '黑屏', 'token', '鉴权', '安全模式', 'Android']
created: 2025-02-18
updated: 2026-03-23
---

## 问题：安卓 RTC Demo摄像头黑屏问题

## 问题详情

**现象**：
运行官方RTC Demo进入音视频房间后摄像头黑屏。

**环境信息**：
- 平台：安卓
- 产品：RTC

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 确认本地运行Android原生Demo
2. 检查日志发现没有SDK日志输出
3. 确认appkey鉴权模式为安全模式
4. 加入房间时未传token导致鉴权失败

## 问题原因

appkey设置为安全模式，加入房间需要传入token鉴权，Demo默认未配置token。

## 解决方案

1. 按照文档获取token：https://doc.yunxin.163.com/nertc/server-apis/TcxNDAxMTI?platform=server
2. 加入房间时传入token参数
3. 或临时将管理后台鉴权模式调整为非安全模式（上线仍需使用token鉴权）。

## 其他触发场景

（合并时在此处追加：`- [安卓] RTC Demo摄像头黑屏问题，来源：['云信-国信网安（上海）大数据科技']，2026-03-23`）
