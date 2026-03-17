---
track_type: 排查类
sub_type: 集成类
product: 呼叫组件
feature: 账号登录
platform: 通用
title: 呼叫组件需要IM账号登录
root_cause: 客户创建的是云信管理账号的子账号,不是IM账号,两者不通用
solution: 呼叫组件必须使用IM账号和密码登录。需要通过服务端API创建IM用户账号,文档:https://doc.yunxin.163.com/messaging2/server-apis/TQyNjgyMzc?platform=server。悬浮窗是应用层能力,纯音视频只提供流数据处理,必须用组件方式才能实现。
customers: ["广州有爱中医门诊部有限公司"]
source: chat_history
tags: ["呼叫组件", "IM账号", "登录", "账号创建"]
created: 2026-02-06
updated: 2026-03-17
---

## 问题：通用 呼叫组件需要IM账号登录

## 问题详情

**现象**：
客户使用云信管理账号的子账号登录呼叫组件失败,提示错误。客户只接了音视频,没有IM,询问是否必须使用IM账号。

## 排查过程

1. 检查账号类型 → 发现是云信管理账号的子账号

**关键发现**：客户创建的是云信管理账号的子账号,不是IM账号,两者不通用

## 问题原因

客户创建的是云信管理账号的子账号,不是IM账号,两者不通用

## 解决方案

呼叫组件必须使用IM账号和密码登录。需要通过服务端API创建IM用户账号,文档:https://doc.yunxin.163.com/messaging2/server-apis/TQyNjgyMzc?platform=server。悬浮窗是应用层能力,纯音视频只提供流数据处理,必须用组件方式才能实现。

## 其他触发场景
