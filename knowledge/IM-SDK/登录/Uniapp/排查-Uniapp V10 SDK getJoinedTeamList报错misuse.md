---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 登录
platform: Uniapp
title: Uniapp V10 SDK getJoinedTeamList报错misuse
root_cause: 客户混用了V9的登录方法和V10的接口，v9和v10不能混用。
solution: V9和V10不能混用。如果是新项目建议直接使用V10，参考V10文档接入；如果需要与旧项目互通，则使用V9。
customers: ['深圳市找大状']
source: chat_history
tags: ['Uniapp', 'V10', 'getJoinedTeamList', 'misuse', 'V9', '登录']
created: 2025-01-23
updated: 2026-03-23
---

## 问题：Uniapp Uniapp V10 SDK getJoinedTeamList报错misuse

## 问题详情

**现象**：
客户使用Uniapp接入IM V10 SDK，调用getJoinedTeamList接口报错misuse，无法获取群聊列表。

## 排查过程

1. 客户反馈getJoinedTeamList接口报错misuse
2. 技术支持建议加try catch打印error
3. 客户反馈catch后还是misuse
4. 客户询问是否引入错误，发送引入的SDK截图
5. 客户确认实例化登录后无法获取群聊
6. 技术支持建议改成await nim.V2NIMTeamService.getJoinedTeamList([1])试试
7. 客户尝试后还是报错
8. 技术支持要求提供最简化demo复现
9. 客户发送代码文件
10. 技术支持发现客户使用的是V9的登录方法
11. 解释v9和v10不能混用，提供V10登录文档
12. 客户询问建议用v9还是v10
13. 因客户老代码是v9，建议用v9
14. 客户发现v9已停止维护，询问是否还建议用
15. 确认是新项目且前后端都重新写后，建议用v10

## 问题原因

客户混用了V9的登录方法和V10的接口，v9和v10不能混用。

## 解决方案

V9和V10不能混用。如果是新项目建议直接使用V10，参考V10文档接入；如果需要与旧项目互通，则使用V9。

## 其他触发场景

（合并时在此处追加）
