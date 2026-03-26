---
track_type: 排查类
sub_type: 集成类
product: 呼叫组件
feature: 登录
platform: Uniapp
title: Uniapp端NIM登录返回192001 connect failed
root_cause: 同账号在多端登录（客服H5+客户Uniapp自定义基座），被踢出导致connect failed
solution: 在云信管理后台开启多端登录功能：IM功能管理 → 基础功能 → 多端登录配置，允许同时多点登录后即可正常登录
customers: ["云信-中山网豹网络科技有限公司"]
source: chat_history
tags: ["192001", "connect failed", "Uniapp", "多端登录", "自定义基座"]
created: 2025-08-26
updated: 2025-08-26
---

## 问题：Uniapp Uniapp端NIM登录返回192001 connect failed

## 问题详情

**现象**：
客户在Uniapp端集成NIM，使用im-uniapp-ui套件，登录时报错：NIM 746 erro 192001 connect failed。日志显示：V2NIMLoginService::login failed, times of login try: 3, err.code: 192001, err.message: connect failed。客丹使用自定义基座，macOS HBuilderX 4.76。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：Uniapp macOS HBuilderX 4.76
- 其他：自定义基座

**相关日志**：
V2NIMLoginService::login failed, times of login try: 3, err.code: 192001, err.message: connect failed

## 排查过程

1. 客服验证账号信息（accid=adcold, appkey=1e80bb934c51c1dd7a594eedfa31bf85）— 客服侧登录成功 → 确认账号正常
2. 排查发现：客户在客服的H5端同时登录同一个账号，导致多端互踢 → 发现多端冲突
3. 客服在控制台开启多端登录开关 → 配置修改
4. 客户重新登录 — 成功 → 问题解决

**关键发现**：客户在客服的H5端同时登录同一个账号，导致多端互踢

## 问题原因

同账号在多端登录（客服H5+客户Uniapp自定义基座），被踢出导致connect failed

## 解决方案

在云信管理后台开启多端登录功能：IM功能管理 → 基础功能 → 多端登录配置，允许同时多点登录后即可正常登录

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
