---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 聊天室
platform: HarmonyOS
title: HarmonyOS获取聊天室成员列表报414 parameter error：memberRoles传空或去掉VIRTUAL角色
root_cause: V2NIM_CHATROOM_MEMBER_ROLE_VIRTUAL虚拟角色参数会导致报参数错误；pageToken和limit参数TypeScript定义没带?必须传值
solution: memberRoles可以传空获取所有类型成员；如需过滤，只用normal/creator/manager等固定成员角色，去掉VIRTUAL虚拟角色参数；pageToken和limit为必填参数需传值
customers: ["武汉盛游"]
source: chat_history
tags: ["HarmonyOS", "聊天室", "getMemberListByOption", "414", "VIRTUAL"]
created: 2025-07-01
updated: 2026-03-25
---

## 问题：HarmonyOS获取聊天室成员列表报414 parameter error：memberRoles传空或去掉VIRTUAL角色

## 问题原因

V2NIM_CHATROOM_MEMBER_ROLE_VIRTUAL虚拟角色参数会导致报参数错误；pageToken和limit参数TypeScript定义没带?必须传值

## 解决方案

memberRoles可以传空获取所有类型成员；如需过滤，只用normal/creator/manager等固定成员角色，去掉VIRTUAL虚拟角色参数；pageToken和limit为必填参数需传值
