---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 通知栏推送
platform: Android
title: OPPO推送新版模板配置方法
root_cause: OPPO推送新版使用模板方式替代channel_id，需要配置category、template_id、template_parameters三个参数，且template_parameters必须为json格式，参数名需与OPPO控制台申请的模板匹配。
solution: 在OPPO控制台申请类别(一般为im)和推送模板，在消息payload的oppoField字段配置category、template_id、template_parameters(json格式)三个参数，与其他字段同级。template_parameters的参数名必须与模板定义一致。
tags: ["OPPO推送", "推送模板", "category", "template_id", "template_parameters", "payload"]
customers: ["南宁思创互联科技有限公司"]
source: chat_history
created: 2026-02-05
updated: 2026-03-17
---

## 问题：Android OPPO推送新版模板配置方法

## 问题详情

**现象**：
OPPO推送改为新版模板方式后，原channel_id配置方式失效，需要配置category、template_id、template_parameters三个参数。配置后推送收不到，报错：syntax error和template_parameters参数错误。

**环境信息**：
- 平台：Android
- SDK版本：NIM SDK 9.21.0
- IM版本：V9

## 排查过程

1. 检查payload配置 → 发现只配置了category
2. 添加template_id和template_parameters → 报错syntax error, pos 1
3. 检查参数格式 → private_title_parameters赋值不对，需要json格式
4. 修改为json格式 → 报错template_parameters no 用户名称
5. 重新申请OPPO模板并正确配置参数 → 推送成功
**关键发现**：OPPO新版推送使用模板方式，需要在控制台申请类别(一般为im)和模板，template_parameters必须为json格式且参数名需与模板匹配。

## 问题原因

OPPO推送新版使用模板方式替代channel_id，需要配置category、template_id、template_parameters三个参数，且template_parameters必须为json格式，参数名需与OPPO控制台申请的模板匹配。

## 解决方案

在OPPO控制台申请类别(一般为im)和推送模板，在消息payload的oppoField字段配置category、template_id、template_parameters(json格式)三个参数，与其他字段同级。template_parameters的参数名必须与模板定义一致。

## 其他触发场景

