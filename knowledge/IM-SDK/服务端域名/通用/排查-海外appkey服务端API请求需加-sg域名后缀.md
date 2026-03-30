---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 服务端域名
platform: 通用
title: 海外appkey服务端API请求需加-sg域名后缀
root_cause: 海外单元（新加坡数据中心）的appkey调用服务端API时必须使用带-sg后缀的域名
solution: 区分appkey服务区域使用不同API域名：海外单元appkey → api-sg.yunxinapi.com；国内单元appkey → api.yunxinapi.com；新版域名已更新但老域名（netease.im）仍可用
customers: ["深圳市掌娱炫动"]
source: chat_history
tags: ["海外appkey","-sg域名","api-sg","服务端API","403"]
created: 2025-08-15
updated: 2026-03-26
---

## 问题：通用 海外appkey服务端API请求需加-sg域名后缀

## 问题详情

**现象**：
客户新应用创建用户报403 forbidden错误，排查发现使用了国内域名。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：通用
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
403 forbidden

## 排查过程

1. 客户提供创建用户接口报错截图 → 确认403错误
2. 客服确认是使用了国内域名 → 定位到域名使用错误
3. 指引改为api-sg.yunxinapi.com → 问题解决

**关键发现**：海外appkey调用服务端API必须使用带-sg后缀的域名

## 问题原因

海外单元（新加坡数据中心）的appkey调用服务端API时必须使用带-sg后缀的域名

## 解决方案

区分appkey服务区域使用不同API域名：
- 海外单元appkey → api-sg.yunxinapi.com
- 国内单元appkey → api.yunxinapi.com
- 新版域名已更新但老域名（netease.im）仍可用

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
