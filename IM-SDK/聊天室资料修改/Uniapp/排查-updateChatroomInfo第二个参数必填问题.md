---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 聊天室资料修改
platform: Uniapp
title: updateChatroomInfo第二个参数必填问题
root_cause: 文档问题：updateChatroomInfo接口实际有两个参数，第二个参数antispamBusinessId当前版本虽理论上非必填，但不传会报错
solution: updateChatroomInfo调用时需要传两个参数，第二个参数antispamBusinessId传空字符串即可：chatroom.V2NIMChatroomService.updateChatroomInfo({...}, {antispamBusinessId: ""})
customers: ['VIP云信-长沙奇喵宇宙网络科技有限公司']
source: chat_history
tags: ['updateChatroomInfo', '聊天室', 'Uniapp', 'antispamBusinessId', '文档问题']
created: 2025-01-06
updated: 2026-03-23
---

## 问题：Uniapp updateChatroomInfo第二个参数必填问题

## 问题详情

**现象**：
客户调用updateChatroomInfo修改聊天室公告时提示无效参数，文档显示只有一个参数但实际需要两个。

## 排查过程

1. 客户尝试只传announcement和serverExtension参数调用updateChatroomInfo
2. 接口返回无效参数错误
3. 技术支持确认文档有误，updateChatroomInfo实际有两个参数
4. 第二个参数antispamBusinessId理论上应非必填，但当前版本需要传入

## 问题原因

文档问题：updateChatroomInfo接口实际有两个参数，第二个参数antispamBusinessId当前版本虽理论上非必填，但不传会报错

## 解决方案

updateChatroomInfo调用时需要传两个参数，第二个参数antispamBusinessId传空字符串即可：chatroom.V2NIMChatroomService.updateChatroomInfo({...}, {antispamBusinessId: ""})

## 其他触发场景

（合并时在此处追加）
