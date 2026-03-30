---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 群组
platform: Electron
title: Electron设置群消息免打扰接口报错
root_cause: 接口调用缺少teamType参数，teamType默认1表示高级群。
solution: setTeamMessageMuteMode接口需要传入三个参数，其中teamType传1表示高级群。
customers: ['深圳市君莫管文化传媒有限公司']
source: chat_history
tags: ['Electron', 'setTeamMessageMuteMode', 'teamType', '群消息免打扰']
created: 2025-01-07
updated: 2026-03-23
---

## 问题：Electron Electron设置群消息免打扰接口报错

## 问题详情

**现象**：
客户调用setTeamMessageMuteMode接口按照示例传参报错，提示要传teamType。

## 排查过程

1. 客户反馈setTeamMessageMuteMode接口按示例传参报错，提示要传teamType
2. 询问teamType有哪几种类型
3. 技术支持回复默认1是高级群
4. 客户发送报错信息截图
5. 技术支持查看后确认应该有三个入参
6. 客户传了1后没报错了

## 问题原因

接口调用缺少teamType参数，teamType默认1表示高级群。

## 解决方案

setTeamMessageMuteMode接口需要传入三个参数，其中teamType传1表示高级群。

## 其他触发场景

（合并时在此处追加）
