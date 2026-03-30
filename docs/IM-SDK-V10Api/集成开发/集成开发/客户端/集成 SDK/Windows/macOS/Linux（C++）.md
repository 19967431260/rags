网易云信即时通讯（NetEase IM）SDK V10（以下简称 NIM SDK）融合了 V9 接口，本文介绍如何集成 NIM Windows/macOS/Linux SDK 到您的项目中。请前往 [资源下载](https://doc.yunxin.163.com/messaging2/resource?platform=all) 页面获取 SDK。

## SDK 目录

为降低接入成本，NIM SDK C++ 封装层使用 CMake 进行管理，根据不同的情况您在接入 C++ 封装层时可能需要适当的修改。SDK 目录拆分为如下结构：

```sh
├─bin
├─include
├─lib
└─wrapper
```

- `bin` 和 `lib` 目录：存放 NIM SDK 的动态库文件，在您发布时请打包使用到的模块，`lib` 后缀为 Windows 下的动态库符号链接文件。
    - `(lib)nim(.dll|.so|.dylib)`：即时通讯，含圈组。
    - `(lib)nim_chatroom(.dll|.so|.dylib)`：聊天室。
    - `(lib)h_available(.dll|.so|.dylib)`：高可用模块，被以上两个模块所依赖。
    - `(lib)nim_tools_http(.dll|.so|.dylib)`：http 工具库，若不使用 `wrapper/nim_tools_cpp_wrapper/nim_tools_http_cpp.h` 中的接口可去除。
    - `nim_audio.dll`：音频解码库，仅支持 Windows 环境，若不使用 `wrapper/nim_tools_cpp_wrapper/nim_audio_cpp.h` 中的接口可去除。
    - `nrtc.dll`：音视频通话库，仅支持 Windows 环境，若不使用 `wrapper/nim_cpp_wrapper/api/nim_cpp_vchat.h` 中的接口可去除。
    - `node-nim.node`：NIM SDK Node 封装层，用于 Electron 以及 Node.js 环境下的接入，其他情况可去除。
    - 其他如 `msvcp120.dll`、`msvcr120.dll` 等（系统）依赖。
- `include` 目录：存放 NIM C SDK 的导出头文件。
- `wrapper` 目录：存放 C++ 封装层的源代码。

<!--
## 以 C 接口接入

如果您希望以纯 C 接口接入 NIM SDK，可通过以下步骤完成接入。
1. 直接添加 include 为头文件搜索路径。
2. 添加 lib 目录为依赖库文件搜索路径。
3. 将 lib 目录下的静态库文件添加为您已有工程的附加依赖库即可使用。

## 以 C++ 接口接入

-->

## 方式一：使用 V10 系列接口

如果您仅使用 V10 接口，只需将 `include` 目录添加到头文件搜索路径，代码中包含对应头文件即可使用，无需进行以下步骤。

## 方式二：基于 CMake 接入

如果您的原工程是基于 CMake 进行管理，可通过以下步骤完成接入。

1. 使用 `add_subdirectory` 命令将 `wrapper` 目录添加为子目录。
2. 使用 `include_directories` 方法将 `include` 和 `wrapper` 文件夹添加为头文件搜索路径。
3. 根据您的执行目标使用 `target_link_libraries` 按需添加链接库即可。库名称分别如下：

   - `nim_cpp_wrapper`：NIM C++ 封装层库。
   - `nim_chatroom_cpp_wrapper`：Chatroom C++ 封装层库。
   - `nim_wrapper_util`：NIM 及 Chatroom C++ 封装层库通用的工具库。
   - `nim_tools_cpp_wrapper`：HTTP 组件 C++ 封装层库。
   - `nim_qchat_cpp_wrapper`：QChat 圈组 C++ 封装层库。

        示例代码如下：

        ```CMake
        # CMakeLists.txt
        cmake_minimum_required(VERSION 3.10)
        project(nim_demo)

        include_directories(${CMAKE_CURRENT_LIST_DIR}/include
                            ${CMAKE_CURRENT_LIST_DIR}/wrapper)
        add_subdirectory(wrapper)
        add_executable(${PROJECT_NAME} main.cpp)
        target_link_libraries(${PROJECT_NAME}
                            nim_cpp_wrapper
                            nim_chatroom_cpp_wrapper
                            nim_wrapper_util
                            nim_tools_cpp_wrapper
                            nim_qchat_cpp_wrapper)
        ```

## 方式三：传统方式接入

传统方式接入是指将 `include` 和 `wrapper` 目录添加到头文件搜索路径中，然后通过 **集成静态库** 或者 **集成源码** 的方式接入。

:::::: div linked-codes
::: code Visual Studio
在界面上选择 **项目 > 属性 > C/C++ > 常规 > 附加包含目录**。
:::
::: code Xcode
在左侧导航栏选择 **导航栏 > 项目 > Build Settings > 搜索** Header Search Paths。
:::
::: code Qt Creator

```Qt
# .pro 文件
INCLUDEPATH += include wrapper
```
:::
::::::

### 方式一：集成静态库

1. 编译 `wrapper` 目录下的源文件生成静态库，产物会输出到 `exports` 目录下。

   :::::: div linked-codes
   ::: code Windows
   ```Bash
   > md build
   > cmake -S wrapper -B build -G "Visual Studio 15 2017 Win64" -DCMAKE_INSTALL_PREFIX=exports
   > cmake --build build --config Release --target install
   ```
   :::
   ::: code macOS
   ```Bash
   > mkdir build
   > cmake -S wrapper -B build -G "Xcode" -DCMAKE_INSTALL_PREFIX=exports
   > cmake --build build --config Release --target install
   ```
   :::
   ::: code Linux
   ```Bash
   > mkdir build
   > cmake -S wrapper -B build -G "Unix Makefiles" -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=exports
   > cmake --build build --config Release --target install
   ```
   :::
   ::::::

   ::: note note

   - 在 `cmake configure` 中添加 `-DCMAKE_CXX_FLAGS_DEBUG=/MTd` 或 `-DCMAKE_CXX_FLAGS_RELEASE=/MT` 生成 MTd/MT 工程。
   - 在 `cmake configure` 中添加 `-DBUILD_SHARED_LIBS=ON` 来生成动态库工程。
   - 在 `cmake configure` 中修改 -G 参数来指定您期望的 generator。
   - 修改命令中的 `Release` 为 Debug 来生成 Debug 版本的库。
   :::

2. 将生成的静态库添加到您项目的链接库中。

    :::::: div linked-codes
    ::: code Visual Studio
    - 右键 **项目 > 链接器 > 常规**，右侧的 **附加库目录** 中添加 exports 为库文件搜索路径。
    - 右键 **项目 > 属性 > 链接器 > 输入 > 附加依赖项** 添加用到的静态库名，如 `nim_cpp_wrapper.lib`，`nim_chatroom_cpp_wrapper.lib`，`nim_wrapper_util.lib`，`nim_tools_cpp_wrapper.lib`，`nim_qchat_cpp_wrapper.lib`。
    :::
    ::: code Xcode
    - 左侧 **导航栏 > 项目 > Build Settings > 搜索** Library Search Paths。
    - 左侧 **导航栏 > 项目 > Build Phases > Link Binary With Libraries** 添加用到的静态库名，如 `libnim_cpp_wrapper.a`。
    :::
    ::: code Qt Creator
    ```Qt
    # .pro 文件
    LIBS += -Lexports -lnim_cpp_wrapper -lnim_chatroom_cpp_wrapper -lnim_wrapper_util -lnim_tools_cpp_wrapper -lnim_qchat_cpp_wrapper
    ```
    :::
    ::::::

### 方式二：集成源码

将 `wrapper` 目录下的源文件添加到您的项目中进行编译。

:::::: div linked-codes
::: code Visual Studio
1. 打开现有的 VS 解决方案。
2. 在解决方案资源管理器中右键单击 **解决方案 > 添加 > 新建项目 > 静态库**。
3. 选择项目类型为静态库。
4. 创建新项目后，在解决方案资源管理器中右键单击该 **项目 > 添加 > 现有项**。
5. 将 `wrapper` 目录下所有源文件添加到项目中。
:::
::: code Xcode
1. 打开现有的 Xcode 项目。
2. 在项目导航栏中右键单击 **项目 > 添加文件** 到 **项目名**。
3. 选择 `wrapper` 目录将其添加到项目中。
:::
::: code Qt Creator

1. 在 Qt Creator 中打开现有项目。
2. 在项目视图中右键单击 **项目 > 添加新建项 > 新建项目**。
3. 选择项目类型为静态库。
4. 创建新项目后，在**项目**视图中右键单击该 **项目 > 添加现有文件**。
5. 将 `wrapper` 目录下所有源文件添加到项目中。
:::
::::::

## 下一步

完成 SDK 接入后，您就可以使用 C++ 封装层的接口进行开发，如下所示：

```C++
#include "nim_cpp_wrapper/nim_cpp_api.h"

int main()
{
    nim::SDKConfig config;
    // 初始化一个即时通讯客户端，appKey 为您在网易云信控制台上创建应用时获取的应用密钥（AppKey）。
    auto ret = nim::Client::Init("appKey", "appDataDir", "", config);
    if(ret != nim::kNIMResSuccess){
        return -1;
    }
    return 0;
}
```

更多详情，请参考 [初始化](https://doc.yunxin.163.com/messaging2/guide/zE1MjkwNTc?platform=client)。

## 添加依赖

运行 SDK 时，您可以按需添加 NIM 动态库依赖和系统依赖。

### 添加 NIM 动态库依赖

- Windows 项目：将 `bin` 目录中用到的动态库文件拷贝到可执行文件所在目录。
- macOS 项目：将 `lib` 目录中用到的动态库文件拷贝到可执行文件的 `runpath` 目录中，对于 app bundle 来说一般为 `Contents/Frameworks` 目录，即将 `runpath` 设置为 `@executable_path/../Frameworks`。
- Linux 项目：将 `lib` 目录中用到的动态库文件拷贝到可执行文件的 `rpath` 目录中，设置 `rpath` 为 `$ORIGIN` 表示可执行文件所在目录。

### 添加系统依赖

- Windows 项目：在 Windows 下，NIM SDK 使用 Visual Studio 2017 及其工具链进行编译。部署应用前，您需要将 Visual Studio 2017 运行时库安装到目标系统中，或将依赖文件存放到执行程序可以搜索到的路径下。下载 Visual Studio 2017 运行时库，请访问 微软官网下载 [vc_redist.x86.exe/vc_redist.x64.exe](https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist?view=msvc-170)。
- macOS 项目：最低系统版本要求 macOS 10.13。
- Linux 项目：最低 glibc 版本要求 2.23。