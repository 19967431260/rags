---
track_type: 排查类
sub_type: 线上事故
product: IM-SDK
feature: 服务端接口
platform: 通用
title: Azure微软云网络故障导致接口超时
root_cause: 微软Azure云网络故障影响云信服务端集群，导致接口响应超时。
solution: 1. 紧急处理：重启调用云信API的进程恢复服务\n2. 长期方案：接入Server SDK双域名灾备方案（https://doc.yunxin.163.com/messaging2/server-apis/jQxNjEwMjI?platform=server），支持域名抖动时实时切换多个备用域名
customers: ["YOOY语音"]
source: chat_history
tags: ["Azure","超时","网络故障","双域名"]
created: 2025-08-19
updated: 2026-03-26
---

## 问题：通用 Azure微软云网络故障导致接口超时

## 问题详情

**现象**：
客户多个项目接口出现超时，Redis锁也出现超时，业务接口响应超过10秒，持续约半小时。云信服务端切换到GCP后问题仍存在，最后通过重启客户进程恢复。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 确认故障现象 → 多项目接口超时，Redis锁超时
2. 排查原因 → 微软Azure云网络故障
3. 尝试切换GCP → 仍有超时
4. 客户重启进程后大部分恢复 → 恢复

**关键发现**：微软Azure云网络故障影响云信服务端集群，导致接口响应超时。

## 问题原因

微软Azure云网络故障影响云信服务端集群，导致接口响应超时。

## 解决方案

1. 紧急处理：重启调用云信API的进程恢复服务
2. 长期方案：接入Server SDK双域名灾备方案（https://doc.yunxin.163.com/messaging2/server-apis/jQxNjEwMjI?platform=server），支持域名抖动时实时切换多个备用域名

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
