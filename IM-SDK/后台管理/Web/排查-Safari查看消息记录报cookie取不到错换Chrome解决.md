---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 后台管理
platform: Web
title: Safari查看消息记录报cookie取不到错换Chrome解决
root_cause: Safari浏览器对云信后台的cookie支持存在问题，导致cookie取不到而报错
solution: 方案1：换用Chrome浏览器访问云信后台查看消息记录；方案2：在Safari设置中删除该域名的cookie后重试
customers: ["南宁市懂卿科技有限公司"]
source: chat_history
tags: ["Safari","cookie","后台消息记录","浏览器兼容性"]
created: 2025-08-27
updated: 2026-03-26
---

## 问题：Web Safari查看消息记录报cookie取不到错换Chrome解决

## 问题详情

**现象**：
客户在云信后台查看指定两账号间消息记录时，用Safari浏览器一进入页面就报错，刷新多次无效。

**复现步骤**：
（无明确步骤，从会话提取）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：Safari浏览器

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客户提供Safari报错截图 → 确认错误
2. 客服询问使用的浏览器 → 获取环境
3. 客户确认Safari → 确认浏览器
4. 客服确认是cookie取不到导致的 → 根因确认
5. 建议换Chrome浏览器重试 → 方案
6. 客户换成Chrome后问题解决 → 验证

**关键发现**：Safari浏览器对云信后台的cookie支持存在问题，导致cookie取不到而报错

## 问题原因

Safari浏览器对云信后台的cookie支持存在问题，导致cookie取不到而报错。

## 解决方案

方案1：换用Chrome浏览器访问云信后台查看消息记录；方案2：在Safari设置中删除该域名的cookie后重试。

## 其他触发场景

（合并时在此处追加）
