本文介绍如何初始化适配面向嵌入式及跨平台场景的即时通讯 C 语言 SDK（简称 NIM SDK）。初始化 SDK 时，可同时配置 APNs 离线推送服务、会话已读多端同步、群消息已读和融合存储等重要功能。

## 调用时机

对 NIM SDK 进行初始化的时机，是在调用各项即时通讯功能之前。一般情况下，在应用的生命周期内，仅需进行一次初始化。

## 前提条件

开始 NIM SDK 初始化前，请确保您已：
- [集成 SDK](https://doc.yunxin.163.com/messaging/guide/zkyNTU1ODU?platform=client)。
- 在 [网易云信控制台](https://app.yunxin.163.com/global/home) 上 [创建应用](https://doc.yunxin.163.com/console/guide/TIzMDE4NTA?platform=console)，并获取 App Key 和 App Secret。
- [注册网易云信 IM 账号](https://doc.yunxin.163.com/messaging2/guide/jU0Mzg0MTU?platform=client#第二步注册-im-账号)，获取 IM 账号和 token。

## 初始化

在使用任何 SDK 接口之前，必须先调用 `nim_client_init` 进行初始化，推荐在应用程序启动时初始化。初始化成功后，即可使用所有的 API。

### 参数说明

参数 | 类型 | 说明
---- | ---- | ---- 
`app_data_dir` | std::string | 应用的数据存储目录，为空则使用默认目录。SDK 自动在该目录下创建数据库等文件。
`app_install_dir` | std::string | SDK 动态库所在的目录全路径，传空字符串即可（SDK 可自动获取）。
`json_extension` | std::string | JSON 扩展配置。

### 示例代码

::: note note 
- 示例中的 JSON 构造与解析示例均使用 [cJSON 库](https://github.com/DaveGamble/cJSON) 实现，您也可以使用其他 C JSON 库（如 yyjson、Jansson 等）完成同样的操作。
- 完整的可运行示例工程请参考 [官方 Sample 仓库](https://github.com/netease-im/nim-embedded-sdk-samples.git)，该仓库包含登录鉴权、好友管理、用户资料、群组管理、云存储、消息收发、会话管理、独立信令、事件订阅等所有模块的完整接入示例，可直接编译运行。
:::

```C
#include "nim_client.h"
#include "nim_client_def.h"
#include <cJSON.h>

// 构造初始化配置 JSON
cJSON* config = cJSON_CreateObject();
cJSON_AddStringToObject(config, kNIMDataBaseEncryptKey, "my_db_key");
char* config_json = cJSON_PrintUnformatted(config);  // => {"db_encrypt_key":"my_db_key"}
cJSON_Delete(config);

// app_data_dir: 数据存储目录名（SDK 自动在该目录下创建数据库等文件）
// app_install_dir: 传空字符串即可（SDK 可自动获取）
// json_extension: JSON 扩展配置
bool ok = nim_client_init("my_app_data", "", config_json);
free(config_json);

if (!ok) {
    // 初始化失败
    return -1;
}

```

## 下一步

完成初始化后，您可以尝试 [登录 IM](https://doc.yunxin.163.com/messaging/guide/Dk1MTY4MzA?platform=client)。