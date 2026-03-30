---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 离线推送
platform: Uniapp
title: UniApp端离线推送调试与参数配置
root_cause: 1. 使用小程序模拟器调试（不支持推送），需用真机+自定义基座运行；2. 服务端发送离线系统通知时只传了基本参数，缺少pushcontent（推送文案）和payload（厂商自定义配置）。
solution: 1. UniApp离线推送必须在真机上调试（模拟器不支持），使用自定义基座（自定义调试基座）运行APP\n2. SDK初始化时设置debugLevel: 'debug'获取详细日志排查\n3. 服务端发送离线系统通知时，必须同时传pushcontent（推送显示文案）和payload（各厂商自定义配置，如标题、跳转方式等）参数，参考：https://doc.yunxin.163.com/messaging/server-apis/DQyNjc5NjE?platform=server
customers: ["二十四小时直聘（天津）信息科技有限责任公司"]
source: chat_history
tags: ["UniApp","离线推送","debugLevel","pushcontent","payload"]
created: 2025-08-22
updated: 2026-03-26
---

## 问题：Uniapp UniApp端离线推送调试与参数配置

## 问题详情

**现象**：
UniApp端离线推送收不到消息，需要调试推送通道是否正常。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 确认调试方式 → 使用debugLevel: 'debug'初始化SDK获取详细日志
2. 确认运行环境 → 小程序模拟器不支持推送，只有真机APP才能注册推送
3. 确认离线系统通知发送问题 → 服务端发送离线系统通知时未传pushcontent和payload参数
4. 指导客户补充参数后问题解决

**关键发现**：使用小程序模拟器调试（不支持推送），需用真机+自定义基座运行；服务端发送离线系统通知时只传了基本参数，缺少pushcontent（推送文案）和payload（厂商自定义配置）。

## 问题原因

使用小程序模拟器调试（不支持推送），需用真机+自定义基座运行；服务端发送离线系统通知时只传了基本参数，缺少pushcontent（推送文案）和payload（厂商自定义配置）。

## 解决方案

1. UniApp离线推送必须在真机上调试（模拟器不支持），使用自定义基座（自定义调试基座）运行APP
2. SDK初始化时设置debugLevel: 'debug'获取详细日志排查
3. 服务端发送离线系统通知时，必须同时传pushcontent（推送显示文案）和payload（各厂商自定义配置，如标题、跳转方式等）参数，参考：https://doc.yunxin.163.com/messaging/server-apis/DQyNjc5NjE?platform=server

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
