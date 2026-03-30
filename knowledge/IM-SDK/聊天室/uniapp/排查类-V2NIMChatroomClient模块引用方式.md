---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 聊天室
platform: Uniapp
title: V2NIMChatroomClient模块引用方式
root_cause: V2NIMChatroomClient是默认导出，应使用import V2NIMChatroomClient from nim-web-sdk-ng/dist/v2/CHATROOM_UNIAPP_SDK，而不是解构语法import {V2NIMChatroomClient} from xxx
solution: Uniapp中正确引入V2NIMChatroomClient：import V2NIMChatroomClient from nim-web-sdk-ng/dist/v2/CHATROOM_UNIAPP_SDK。注意是默认导出，不要使用{}解构语法
customers: ['东莞市云特信息科技有限公司']
source: chat_history
tags: ['聊天室', 'Uniapp', 'V2NIMChatroomClient', '引入', '模块']
created: 2025-01-07
updated: 2026-03-23
---

## 问题：V2NIMChatroomClient模块引用方式

## 问题详情

**现象**：
客户在Uniapp项目中引用V2NIMChatroomClient时出错，不清楚正确的引入路径

## 排查过程

1. 客户尝试从nim-web-sdk-ng/dist/esm/nim引入失败
2. 客服提供正确路径：nim-web-sdk-ng/dist/v2/CHATROOM_UNIAPP_SDK
3. 客户使用import {V2NIMChatroomClient} from xxx方式仍报错
4. 发现不应放在{}解构中
关键发现：V2NIMChatroomClient是默认导出，不应使用解构语法

## 问题原因

V2NIMChatroomClient是默认导出，应使用import V2NIMChatroomClient from nim-web-sdk-ng/dist/v2/CHATROOM_UNIAPP_SDK，而不是解构语法import {V2NIMChatroomClient} from xxx

## 解决方案

Uniapp中正确引入V2NIMChatroomClient：import V2NIMChatroomClient from nim-web-sdk-ng/dist/v2/CHATROOM_UNIAPP_SDK。注意是默认导出，不要使用{}解构语法

## 其他触发场景

（合并时在此处追加）
