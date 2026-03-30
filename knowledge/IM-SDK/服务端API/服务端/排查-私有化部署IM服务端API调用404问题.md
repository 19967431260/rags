---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 服务端API
platform: 服务端
title: 私有化部署IM服务端API调用404问题
root_cause: 私有化部署的服务端API路径与公有云不同，需要在路径中添加/nimserver前缀。
solution: 私有化部署调用IM服务端API时，URL路径需要加上/nimserver前缀，如：http://ip:port/nimserver/im/v2/accounts。
customers: ['北京中软融鑫计算机系统工程有限公司']
source: chat_history
tags: ['IM', '私有化部署', '服务端API', '404', 'nimserver']
created: 2025-02-11
updated: 2026-03-23
---

## 问题：服务端 私有化部署IM服务端API调用404问题

## 问题详情

**现象**：
客户私有化部署IM后，调用服务端创建账号接口返回404错误，无法找到对应服务。

**环境信息**：
- 平台：服务端
- 产品：IM-SDK

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客户使用http://10.168.188.121:10081/im/v2/accounts调用 → 返回404
2. 检查postman请求格式 → body使用raw格式，应改为json
3. 实施同事确认接口路径 → 需要添加/nimserver前缀
4. 修正路径为/nimserver/im/v2/accounts → 请求成功

## 问题原因

私有化部署的服务端API路径与公有云不同，需要在路径中添加/nimserver前缀。

## 解决方案

私有化部署调用IM服务端API时，URL路径需要加上/nimserver前缀，如：http://ip:port/nimserver/im/v2/accounts。

## 其他触发场景

（合并时在此处追加：`- [服务端] 私有化部署IM服务端API调用404问题，来源：['北京中软融鑫计算机系统工程有限公司']，2026-03-23`）
