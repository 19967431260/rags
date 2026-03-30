网易云信即时通讯 C SDK（NetEase Instant Messaging SDK，简称 NIM SDK）为面向嵌入式及跨平台场景的即时通讯 C 语言开发组件。本文档介绍如何在您的 C 项目中集成 SDK，实现核心功能调用。

## 平台支持

SDK 采用纯 C 接口设计（C99 标准），无 C++ 运行时依赖，适合在资源受限的嵌入式设备及各类操作系统上集成。

NIM C SDK 支持以下的平台及架构：

平台 | 架构 | 最低版本
--- | --- | ---
Windows	| x86/x86_64	| Windows 7+
macOS | x86_64/arm64 | 10.13+
Linux | x86_64/arm/aarch64/mips/mips64/riscv32 | GCC 4.9+
iOS | arm64/armv7 | 9.0+
Android | armeabi-v7a/arm64-v8a/x86/x86_64 | API 21+
HarmonyOS | arm64-v8a | 5.0+

::: note note 
如需在其他嵌入式平台（如 RTOS、OpenWrt、自定义 Linux 等）使用，您可 [提交工单](https://app.yunxin.163.com/global/service/ticket/create) 获取工具链适配支持。
:::

## 开发环境

- CMake ≥ 3.19
- C 编译器：GCC、Clang 或 MSVC 

## 前提条件

根据本文操作前，请确保您已经完成了以下设置，以用在下文第四步功能测试阶段：

- 在 [网易云信控制台](https://app.yunxin.163.com/global/home) 上，[创建应用](https://doc.yunxin.163.com/console/guide/TIzMDE4NTA?platform=console)，获取 App Key 和 App Secret。
- [注册网易云信 IM 账号](https://doc.yunxin.163.com/messaging2/guide/jU0Mzg0MTU?platform=client#%E7%AC%AC%E4%BA%8C%E6%AD%A5%E6%B3%A8%E5%86%8C-im-%E8%B4%A6%E5%8F%B7)，获取 IM 账号和 Token。

## 获取 SDK

1. 通过 [官网](https://doc.yunxin.163.com/messaging2/resource?platform=linux) 下载对应平台的 NIM C SDK 预编译包。

2. 解压 SDK 包到任意目录，目录结构大致如下：

    ```
    nim-sdk/
    ├── include/                       # 头文件
    │   └── nim/
    └── lib/
        ├── libnim.dylib               # macOS 动态库（Windows: nim.dll，Linux: libnim.so）
        └── cmake/
            └── NIM/
                ├── NIMConfig.cmake
                ├── NIMConfigVersion.cmake
                └── NIMTargets.cmake

    ```

## 集成 SDK

SDK 提供标准的 CMake 配置文件，推荐使用 `find_package` 方式集成。

**CMakeLists.txt 示例：**

```
cmake_minimum_required(VERSION 3.19)
project(my_app LANGUAGES C)

# 查找 NIM SDK
find_package(NIM REQUIRED COMPONENTS nim)

# 创建可执行文件
add_executable(my_app main.c)
target_link_libraries(my_app PRIVATE NIM::nim)
```

1. 构建命令。

    ```
    # 配置 — 将 /path/to/nim-sdk 替换为 SDK 解压路径
    cmake -B build -DCMAKE_PREFIX_PATH=/path/to/nim-sdk

    # 编译
    cmake --build build
    ```

2. 引用头文件。

    在代码中包含总头文件即可使用所有模块 API：

    ```
    #include "nim_sdk_api.h"
    ```

    或按需引入单个模块：

    ```
    #include "nim_client.h"    // 登录鉴权
    #include "nim_talk.h"      // 消息收发
    #include "nim_friend.h"    // 好友管理
    #include "nim_user.h"      // 用户资料
    #include "nim_team.h"      // 群组管理
    #include "nim_nos.h"       // 云存储
    #include "nim_session.h"   // 会话管理
    #include "nim_signaling.h" // 独立信令
    #include "nim_subscribe_event.h" // 事件订阅
    ```