---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 私有化部署
platform: Web
title: V10 Web私有化http+ws连接配置
root_cause: V10 Web端默认使用https+wss，需要显式配置websdkSsl为false才能使用http+ws。
solution: 初始化第二参数配置：privateConf: { appkey: 'xxx', websdkSsl: false, weblbsUrl: 'http://ip:port/lbs/webconf.jsp', link_web: 'ip:port' }，其中websdkSsl为false代表开启http+ws连接。
customers: ['云信-宏信动力(北京)科技有限公司']
source: chat_history
tags: ['私有化', 'Web', 'http', 'ws', 'websdkSsl', 'V10']
created: 2025-02-08
updated: 2026-03-23
---

## 问题：Web V10 Web私有化http+ws连接配置

## 问题详情

**现象**：
V10 Web端私有化环境可以配置使用http+ws连接，避免SSL证书问题。

**环境信息**：
- 平台：Web
- 产品：IM-SDK

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

私有化环境没有SSL证书，需要配置http+ws连接
配置后仍然连接失败

## 问题原因

V10 Web端默认使用https+wss，需要显式配置websdkSsl为false才能使用http+ws。

## 解决方案

初始化第二参数配置：privateConf: { appkey: 'xxx', websdkSsl: false, weblbsUrl: 'http://ip:port/lbs/webconf.jsp', link_web: 'ip:port' }，其中websdkSsl为false代表开启http+ws连接。

## 其他触发场景

（合并时在此处追加：`- [Web] V10 Web私有化http+ws连接配置，来源：['云信-宏信动力(北京)科技有限公司']，2026-03-23`）
