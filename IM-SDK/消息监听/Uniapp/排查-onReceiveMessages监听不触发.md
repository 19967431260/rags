---
track_type: 排查类
sub_type: 功能实现咨询
product: IM-SDK
feature: 消息监听
platform: Uniapp
title: onReceiveMessages监听不触发
root_cause: 监听注册时机不正确或监听写法错误
solution: 确保在初始化成功后注册监听，且监听写法正确：nim.V2NIMMessageService.on("onReceiveMessages", function(messages) { console.log('收到消息', messages); })。注意这是接收其他人发来的消息才会触发，自己发的不触发
customers: ["长沙兴超教育咨询有限公司"]
source: chat_history
tags: ["IM V10","Uniapp","消息监听","回调"]
created: 2025-05-05
updated: 2025-03-23
---

## 问题：Uniapp onReceiveMessages监听不触发

## 问题详情

**现象**：
客户注册onReceiveMessages监听后，收到消息时没有触发回调。

**环境信息**：
- 平台：Uniapp
- 功能：消息监听

## 排查过程

1. 确认问题现象 → 监听不触发
2. 检查监听注册时机 → 是否在初始化成功后注册
3. 检查监听写法 → 是否正确
4. 确认触发条件 → 只接收其他人发来的消息

**关键发现**：监听注册时机或写法可能不正确

## 问题原因

1. 监听注册时机不正确
2. 监听写法错误
3. 误解触发条件（自己发的消息不会触发）

## 解决方案

1. **确保注册时机**：确保在初始化成功后注册监听
2. **正确监听写法**：
   ```javascript
   nim.V2NIMMessageService.on("onReceiveMessages", function(messages) {
     console.log('收到消息', messages);
   });
   ```
3. **注意触发条件**：这是接收其他人发来的消息才会触发，自己发的不触发

## 其他触发场景

