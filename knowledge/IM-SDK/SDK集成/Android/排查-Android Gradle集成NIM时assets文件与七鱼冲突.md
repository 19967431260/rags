---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: SDK集成
platform: Android
title: Android Gradle集成NIM时assets文件与七鱼冲突
root_cause: 七鱼客服SDK与NIM SDK使用了相同的资源文件（assets/nim/*），包名不同但assets文件路径冲突
solution: 在build.gradle中添加exclude规则：exclude 'assets/nim/*'、exclude 'assets/nim/rsa/*'、exclude 'assets/nim/sm2/*'；彻底解决需七鱼侧做兼容适配
customers: ["广东苗仓"]
source: chat_history
tags: ["Android", "Gradle", "assets冲突", "七鱼", "exclude", "SDK集成"]
created: 2025-07-01
updated: 2025-07-25
---

## 问题：Android Gradle集成NIM时assets文件与七鱼冲突

## 问题详情

**现象**：
客户升级Gradle后运行出现assets文件冲突，SDK初始化异常。加入exclude规则排除assets/nim/*等文件后正常运行，功能测试暂未发现问题。

**环境信息**：
- 集成方式：Gradle
- 同时使用：云信NIM SDK + 七鱼客服SDK

## 排查过程

1. 客户提供截图确认冲突现象（jar包冲突相关错误）
2. 检查依赖树未发现直接重复引入
3. 发现客户同时使用了七鱼客服SDK
4. 确认为七鱼使用云信开源代码修改包名，导致assets下nim相关文件重复

**关键发现**：七鱼客服SDK与NIM SDK使用了相同的资源文件（assets/nim/*），包名不同但assets文件路径完全相同，导致文件覆盖冲突。

## 问题原因

七鱼客服SDK基于云信开源代码修改了包名（将`com.netease`*改为`com.qiyukf`*），但assets目录结构保留不变，导致assets/nim/*等文件与NIM SDK原始文件路径冲突。

## 解决方案

1. 在build.gradle中添加exclude规则排除冲突的assets文件：
   ```
   android {
       packagingOptions {
           exclude 'assets/nim/*'
           exclude 'assets/nim/rsa/*'
           exclude 'assets/nim/sm2/*'
       }
   }
   ```
2. 充分测试exclude之后的功能是否正常
3. 彻底解决需七鱼侧对冲突文件做兼容适配
