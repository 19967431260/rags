---
track_type: 排查类
sub_type: 集成类
product: 呼叫组件
feature: 音视频通话
platform: Windows
title: PC呼叫组件token鉴权问题
root_cause: PC呼叫组件token获取实现与移动端不同，移动端呼叫组件内部处理了token获取，PC端需要自行实现token获取逻辑。
solution: 1. PC呼叫组件需要按照token接入方案自行实现token获取
2. 参考文档：https://doc.yunxin.163.com/nertc/server-apis/TcxNDAxMTI?platform=server
3. 替换demo中默认的token获取URL为自己的应用服务器
4. 确保获取token的uid与客户端加入房间的uid一致（注意accid和呼叫组件uid的区别）。
customers: ['云信-广州群市网络科技有限公司']
source: chat_history
tags: ['呼叫组件', 'token', '鉴权', 'Windows', '音视频']
created: 2025-02-21
updated: 2026-03-23
---

## 问题：Windows PC呼叫组件token鉴权问题

## 问题详情

**现象**：
手机和电脑同时登录同一账号，手机通话正常，PC可接通但手机显示通话中。

**环境信息**：
- 平台：Windows
- 产品：呼叫组件

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 确认测试场景：手机给电脑账号发起视频通话
2. 手机显示接通中，电脑进入正常通话状态
3. 查看日志发现PC端加入音视频房间时token鉴权错误
4. 检查token获取实现方式

## 问题原因

PC呼叫组件token获取实现与移动端不同，移动端呼叫组件内部处理了token获取，PC端需要自行实现token获取逻辑。

## 解决方案

1. PC呼叫组件需要按照token接入方案自行实现token获取
2. 参考文档：https://doc.yunxin.163.com/nertc/server-apis/TcxNDAxMTI?platform=server
3. 替换demo中默认的token获取URL为自己的应用服务器
4. 确保获取token的uid与客户端加入房间的uid一致（注意accid和呼叫组件uid的区别）。

## 其他触发场景

（合并时在此处追加：`- [Windows] PC呼叫组件token鉴权问题，来源：['云信-广州群市网络科技有限公司']，2026-03-23`）
