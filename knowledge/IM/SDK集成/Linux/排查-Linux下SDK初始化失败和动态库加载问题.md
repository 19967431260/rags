---
track_type: 排查类
sub_type: 使用问题
product: IM
feature: SDK集成
platform: Linux
title: "Linux下SDK初始化失败和动态库加载问题"
root_cause: "Linux系统下可执行程序搜索动态库的路径默认不包含当前目录，需要设置RPATH。Qt的pro文件中$ORIGIN需要特殊转义。"
solution: "在Qt的.pro文件中添加：
```
QMAKE_LFLAGS += -Wl,-rpath,\$\$ORIGIN/.
```
注意：
1. 使用$$转义$符号
2. 末尾加.表示当前目录
3. 所有so文件放到与可执行程序同级目录
4. 使用readelf -d验证：readelf -d 可执行程序 | grep runpath"
customers: ["上海会畅"]
source: chat_history
tags: ["Linux", "RPATH", "动态库加载", "Qt", "$ORIGIN", "UOS"]
created: 2026-01-13
updated: 2026-03-15
---

## 问题：Linux Linux下SDK初始化失败和动态库加载问题

## 问题详情

**现象**：
客户在UOS系统下集成IM SDK，使用Qt开发，初始化失败。Windows和Mac平台相同代码正常，Linux下失败。

## 排查过程

1. 检查动态库加载 → ldd查看依赖关系
2. 检查RPATH设置 → Linux可执行程序默认不搜索当前目录
3. 设置RPATH为$ORIGIN → 需要注意转义问题
4. Qt的pro文件配置 → QMAKE_LFLAGS += -Wl,-rpath,\$\$ORIGIN/.

## 问题原因

Linux系统下可执行程序搜索动态库的路径默认不包含当前目录，需要设置RPATH。Qt的pro文件中$ORIGIN需要特殊转义。

## 解决方案

在Qt的.pro文件中添加：
```
QMAKE_LFLAGS += -Wl,-rpath,\$\$ORIGIN/.
```
注意：
1. 使用$$转义$符号
2. 末尾加.表示当前目录
3. 所有so文件放到与可执行程序同级目录
4. 使用readelf -d验证：readelf -d 可执行程序 | grep runpath

## 其他触发场景

（暂无）
