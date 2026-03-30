---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 群组
platform: Server
title: 服务端创建群返回414 bad members
root_cause: 创建群时成员数量可能超出/team/add.action接口的单次添加上限，导致bad members报错
solution: /team/add.action接口创建群有成员数量限制，超限后需分批添加或使用其他接口；问题账号自行重试后成功
customers: ["上海汇绿电子商务有限公司"]
source: chat_history
tags: ["414","bad members","创建群","/team/add.action","Server"]
created: 2025-08-07
updated: 2026-03-26
---

## 问题：Server 服务端创建群返回414 bad members

## 问题详情

**现象**：
服务端调用/team/add.action接口创建群时返回{"code":414,"desc":"bad members"}，排查发现所有成员账号均已在云信平台注册。

**复现步骤**：
（无明确步骤，从会话提取）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客户提供414 bad members错误截图 → 确认错误信息
2. 客服要求提供members参数内容 → 获取参数
3. 客户提供完整accid列表 → 确认成员
4. 客服查询确认所有账号有效 → 排除账号问题
5. 客服确认使用的API是/team/add.action → 确认接口
6. 客户重试后成功 → 临时恢复
7. 客户自述可能之前人数超限 → 根因推测

**关键发现**：创建群时成员数量可能超出/team/add.action接口的单次添加上限，导致bad members报错

## 问题原因

创建群时成员数量可能超出/team/add.action接口的单次添加上限，导致bad members报错。

## 解决方案

/team/add.action接口创建群有成员数量限制，超限后需分批添加或使用其他接口；问题账号自行重试后成功。

## 其他触发场景

（合并时在此处追加）
