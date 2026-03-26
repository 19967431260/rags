---
track_type: 排查类
sub_type: 集成类
product: RTC
feature: 部署
platform: Server
title: 私有化后台登录失败getChecksum error
root_cause: 域名证书在天翼云负载均衡上过期，导致 HTTPS 校验失败，getChecksum 接口调用异常
solution: 登录天翼云负载均衡控制台，更新域名证书。如直接更新失败，可删除原配置后重新创建一个 HTTPS 监听器并配置新证书。
customers: ["河北元造宙"]
source: chat_history
tags: ["getChecksum error","证书过期","天翼云","HTTPS","登录失败"]
created: 2025-08-19
updated: 2026-03-26
---

## 问题：Server 私有化后台登录失败getChecksum error

## 问题详情

**现象**：
客户登录私有化评标系统时页面弹出 Error: getChecksum error，无法进入系统。更换房间号仍然不能进入。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客服排查发现录制的 room already has running record task → 进一步排查
2. 检查日志发现接口报错 → 定位接口层问题
3. 最终确认为域名证书过期导致 → 根因确认

**关键发现**：域名证书在天翼云负载均衡上过期，导致 HTTPS 校验失败，getChecksum 接口调用异常

## 问题原因

域名证书在天翼云负载均衡上过期，导致 HTTPS 校验失败，getChecksum 接口调用异常

## 解决方案

登录天翼云负载均衡控制台，更新域名证书。如直接更新失败，可删除原配置后重新创建一个 HTTPS 监听器并配置新证书。

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
