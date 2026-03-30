NERoom 房间组件支持配置回调，方便您接收重要事件消息。当事件被触发时，回调主动推送事件内容到您配置的回调地址。本文介绍 NERoom 房间事件的参数说明和响应消息 JSON 示例。

::: note notice
开通消息的操作步骤，请参考 [开通消息抄送](https://doc.yunxin.163.com/neroom/server-apis/zYxNzIzMTE?platform=server)。
:::

<style>
table th:first-of-type {width: 25%;}
table th:nth-of-type(2) {width: 20%;}
table th:nth-of-type(3) {width: 55%;}
</style>

## 创建及关闭房间

- **消息体**

    字段 | 类型 | 说明
    ---- | ---- | ----
    requestId | String | 抄送事件的唯一标识。 |
    eventType | String | 事件类型：<ul><li>创建房间：`CREATE_ROOM`</li><li>关闭房间：`CLOSE_ROOM`</li></ul> |
    timestamp | Number | 事件发生的 UTC 时间戳，从 1970 年 1 月 1 日 0 点 0 分 0 秒开始到现在的毫秒数。 |
    body | JSON | 消息体。 |
      roomArchiveId | String | 归档到历史记录中的房间 ID，全局唯一，最大长度为 36 个字符。 |
      roomUuid | String | 房间标识，应用内进行中的房间唯一编号，最大长度为 64 字符。 |
      operatorUserUuid | Number | 操作人的用户标识。 |

- **示例**

    ```JSON
    {
        "requestId":"fdaac90ddfda4c8998c952719c21e2a0",
        "eventType":"CREATE_ROOM",
        "timestamp":1648006285198,
        "body":{
            "roomArchiveId":"2331",
            "roomUuid":"12345",
            "operatorUserUuid":"***"
        }
    }
    ```

## 用户加入及离开房间

- **消息体**

    字段 | 类型 | 说明
    ---- | ---- | ----
    requestId | String | 抄送事件的唯一标识。 |
    eventType | String | 事件类型：<ul><li>加入房间：`USER_JOIN_ROOM` </li><li>离开房间：`USER_LEAVE_ROOM`</li></ul> |
    timestamp | Number | 事件发生的 UTC 时间戳，从 1970 年 1 月 1 日 0 点 0 分 0 秒开始到现在的毫秒数。 |
    body | JSON | 消息体。 |
      roomArchiveId | String | 归档到历史记录中的房间 ID，全局唯一，最大长度为 36 个字符。 |
      roomUuid | String | 房间标识，应用内进行中的房间唯一编号，最大长度为 64 字符。 |
      users | JSONArray | 用户信息。 |
        role | String | 用户角色。 |
        userUuid | String | 用户标识。 |

- **示例**

    ```JSON
    {
        "requestId":"7b6319d1cb5e430e94642bd5ecd0b8ff",
        "eventType":"USER_JOIN_ROOM",
        "timestamp":1648005754358,
        "body":{
            "roomArchiveId":"2331",
            "roomUuid":"12345",
            "users":[
                {
                    "role":"host",
                    "userUuid":"test"
                }
            ]
        }
    }
    ```

## 成员角色变更

- **消息体**

    字段 | 类型 | 说明
    ---- | ---- | ----
    requestId | String | 抄送事件的唯一标识。 |
    eventType | String | 事件类型，固定为 `USER_ROLE_CHANGE`。 |
    timestamp | Number | 事件发生的 UTC 时间戳，从 1970 年 1 月 1 日 0 点 0 分 0 秒开始到现在的毫秒数。 |
    body | JSON | 消息体。 |
      roomArchiveId | String | 归档到历史记录中的房间 ID，全局唯一，最大长度为 36 个字符。 |
      roomUuid | String | 房间标识，应用内进行中的房间唯一编号，最大长度为 64 字符。 |
      userUuid | String | 用户的标识。 |
      oldRole | String | 修改前用户角色。 |
      newRole | String | 修改后用户角色。 |
      operatorUserUuid | String | 操作人的用户标识。 |

- **示例**

    ```JSON
    {
        "requestId":"a0b855ceb96649f79ec967dc55209fea",
        "eventType":"USER_ROLE_CHANGE",
        "timestamp":1648007060510,
        "body":{
            "roomArchiveId":"2331",
            "roomUuid":"12345",
            "userUuid":"test1",
            "oldRole":"host",
            "newRole":"student",
            "operatorUserUuid":"test1"
        }
    }
    ```

## 成员昵称变更

- **消息体**

    字段 | 类型 | 说明
    ---- | ---- | ----
    requestId | String | 抄送事件的唯一标识。 |
    eventType | String | 事件类型，固定为 `USER_NAME_CHANGE`。 |
    timestamp | Number | 事件发生的 UTC 时间戳，从 1970 年 1 月 1 日 0 点 0 分 0 秒开始到现在的毫秒数。 |
    body | JSON | 消息体。 |
      roomArchiveId | String | 归档到历史记录中的房间 ID，全局唯一，最大长度为 36 个字符。 |
      roomUuid | String | 房间标识，应用内进行中的房间唯一编号，最大长度为 64 字符。 |
      userUuid | String | 用户的标识。 |
      oldUserName | String | 修改前用户名字。 |
      newUserName | String | 修改后用户名字。 |
      operatorUserUuid | String | 操作人的用户标识。 |

- **示例**

    ```JSON
    {
        "requestId":"a0b855ceb96649f79ec967dc55209fea",
        "eventType":"USER_NAME_CHANGE",
        "timestamp":1648007048918,
        "body":{
            "roomArchiveId":"2331",
            "roomUuid":"12345",
            "userUuid":"***",
            "oldUserName":"test01",
            "newUserName":"test04",
            "operatorUserUuid":"***"
        }
    }
    ```

## 录制文件可下载信息事件

当录制文件生成完毕，并且上传到点播系统成功后发出本次回调。

- **消息体**

    字段 | 类型 | 说明
    ---- | ---- | ----
    requestId | String | 抄送事件的唯一标识。 |
    eventType | String | 事件类型，固定为 `RTC_RECORD`。 |
    timestamp | Number | 事件发生的 UTC 时间戳，从 1970 年 1 月 1 日 0 点 0 分 0 秒开始到现在的毫秒数。 |
    body | JSON | 消息体。 |
      roomArchiveId | String | 归档到历史记录中的房间 ID，全局唯一，最大长度为 36 个字符。 |
      roomUuid | String | 房间标识，应用内进行中的房间唯一编号，最大长度为 64 字符。 |
      userUuid | String | 单人录制（`mix` 字段为 `false`）时的用户标识，混录（`mix` 字段为 `true`）时为空。 |
      type | String | 文件的类型，即文件扩展名。包括：<ul><li>aac：实时音频录制文件。</li><li>mp4：实时视频录制文件。</li><li>flv：互动直播视频录制文件。</li></ul> |
      mix | Boolean | 是否为混合录制文件。<ul><li>true：混合录制文件。</li><li>false：单人录制文件。</li></ul> |
      filename | String | 文件名，直接存储，混合录制文件 filename 带有 `-mix` 标记。 |
      md5 | String | 文件的 MD5 值。 |
      url | String | 文件的下载地址。 |
      size | Number | 文件大小，单位为字节。 |
      vid | Number | 点播文件 ID，通过该参数可以调用点播接口查询相关信息。 |
      pieceIndex | Number | 录制文件的切片索引，如果单通通话录制时长超过切片时长，则录制文件会被且被切割成多个文件。 |
      timestamp | Number | 录制文件生成的 UTC 时间戳。单位：毫秒。 |

- **示例**

    ```JSON
    {
        "requestId":"a0b855ceb96649f79ec967dc55209fea",
        "eventType":"RTC_RECORD",
        "timestamp":1648007048918,
        "body":{
            "roomArchiveId":"1afd234521",
            "roomUuid":"12345",
            "userUuid":"***",
            "type":"mp4",
            "mix":false,
            "filename":"0-51657353189055-1606***78-0-mix.mp4",
            "md5":"e66ff965e0f***245dd0",
            "size":1232132,
            "url":"http://..126.net/***/0-51657353189055-1606***978-0-mix.mp4",
            "vid": 3333091818,
            "pieceIndex":0,
            "timestamp":1606974909978
        }
    }
    ```

## 白板录制完成事件

当白板录制文件生成完毕，并且上传到点播系统成功后发出本次回调。

- **消息体**

    字段 | 类型 | 说明
    ---- | ---- | ----
    requestId | String | 抄送事件的唯一标识。 |
    eventType | String | 事件类型，固定为 `WHITEBOARD_RECORD`。 |
    timestamp | Number | 事件发生的 UTC 时间戳，从 1970 年 1 月 1 日 0 点 0 分 0 秒开始到现在的毫秒数。 |
    body | JSON | 消息体。 |
      roomArchiveId | String | 归档到历史记录中的房间 ID，全局唯一，最大长度为 36 个字符。 |
      roomUuid | String | 房间标识，应用内进行中的房间唯一编号，最大长度为 64 字符。 |
      filename | String | 文件名。 |
      md5 | String | 文件的 MD5 值。 |
      size | Number | 文件大小，单位为字节。 |
      url | String | 文件的下载地址。 |
      recordTime | Number | 录制时间戳，单位：毫秒。 |
      timestamp | Number | 录制文件生成的系统时间戳，单位：毫秒。 |

- **示例**

    ```JSON
    {
        "requestId":"a0b855ceb96649f79ec967dc55209fea",
        "eventType":"WHITEBOARD_RECORD",
        "timestamp":1648007048918,
        "body":{
            "roomArchiveId":"2331",
            "roomUuid":"12345",
            "filename":"0-51657353189055-1606***78-0.gz",
            "md5":"e66ff965e0f***245dd0",
            "size":1232132,
            "url":"http://..126.net/***/0-51657353189055-1606***978-0.gz",
            "recordTime":1606974904978，
            "timestamp":1606974909978
        }
    }
    ```

## 麦位非法推流事件

在开启了防炸麦检测功能后，NERoom 会在检测到可疑推流用户后抄送麦位非法推流事件。

- **消息体**

    字段 | 类型 | 说明
    ---- | ---- | ----
    request_id | String | 抄送事件的唯一标识。 |
    event_type | String | 事件类型，固定为 `SEAT_ILLEGAL_PUB_STREAM`。 |
    timestamp | Number | 事件发生的 UTC 时间戳，从 1970 年 1 月 1 日 0 点 0 分 0 秒开始到现在的毫秒数。 |
    body | JSON | 消息体。 |
      room_archive_id | String | 归档到历史记录中的房间 ID，全局唯一，最大长度为 36 个字符。 |
      user_uuid | String | 用户标识。
      rtc_uid | Number | RTC 用户账号。 |
      rtc_cid | String | RTC 频道标识。 |

- **示例**

    ```JSON
    {
        "request_id":"fdaac90ddfda4c8998c952719c21e2a0",
        "event_type":"SEAT_ILLEGAL_PUB_STREAM",
        "timestamp":1648006285198,
        "body":{
            "room_archive_id":"2331",
            "user_uuid":"***",
            "rtc_uid":123, // RTC 的账号
            "rtc_cid":"" // RTC 的房间
        }
    }
    ```

## 成员音频打开

- **消息体**

     字段 | 类型 | 说明 |
    --- | --- | --- |
     requestId | String | 抄送事件的唯一标识。 |
     eventType | String | 事件类型，固定为 `USER_AUDIO_ON`。 |
     timestamp | Number | 事件发生或抄送的时间戳，单位为毫秒。 |
     body | JSON | 消息体。 |
      roomArchiveId | String | 房间归档 ID，NERoom 房间组件会保证全局唯一，最大长度为 36 个字符。 |
      roomUuid | String | 房间标识，由您传入，NERoom 房间组件不保证全局唯一，您可自行保证 ID 唯一性，最大长度为 64 字符。 |
      userUuid | String | 用户标识。 |

- **示例**

    ```JSON
    {
        "requestId":"a0b855ceb96649f79ec967dc55209fea",
        "eventType":"USER_AUDIO_ON",
        "timestamp":1648007048918,
        "body":{
            "roomArchiveId":"2331",
            "roomUuid":"12345",
            "userUuid":"someone",
        }
    }
    ```

## 成员音频关闭

- **消息体**

     字段 | 类型 | 说明 |
    --- | --- | --- |
     requestId | String | 抄送事件的唯一标识。 |
     eventType | String | 事件类型，固定为 `USER_AUDIO_OFF`。 |
     timestamp | Number | 事件发生或抄送的时间戳，单位为毫秒。 |
     body | JSON | 消息体。 |
      roomArchiveId | String | 房间归档 ID，NERoom 房间组件会保证全局唯一，最大长度为 36 个字符。 |
      roomUuid | String | 房间标识，由您传入，NERoom 房间组件不保证全局唯一，您可自行保证 ID 唯一性，最大长度为 64 字符。 |
      userUuid | String | 用户标识。 |

- **示例**

    ```JSON
    {
        "requestId":"a0b855ceb96649f79ec967dc55209fea",
        "eventType":"USER_AUDIO_OFF",
        "timestamp":1648007048918,
        "body":{
            "roomArchiveId":"2331",
            "roomUuid":"12345",
            "userUuid":"someone",
        }
    }
    ```

## 成员视频打开

- **消息体**

     字段 | 类型 | 说明 |
    --- | --- | --- |
     requestId | String | 抄送事件的唯一标识。 |
     eventType | String | 事件类型，固定为 `USER_VIDEO_ON`。 |
     timestamp | Number | 事件发生或抄送的时间戳，单位为毫秒。 |
     body | JSON | 消息体。 |
      roomArchiveId | String | 房间归档 ID，NERoom 房间组件会保证全局唯一，最大长度为 36 个字符。 |
      roomUuid | String | 房间标识，由您传入，NERoom 房间组件不保证全局唯一，您可自行保证 ID 唯一性，最大长度为 64 字符。 |
      userUuid | String | 用户标识。 |

- **示例**

    ```JSON
    {
        "requestId":"a0b855ceb96649f79ec967dc55209fea",
        "eventType":"USER_VIDEO_ON",
        "timestamp":1648007048918,
        "body":{
            "roomArchiveId":"2331",
            "roomUuid":"12345",
            "userUuid":"someone",
        }
    }
    ```

## 成员视频关闭

- **消息体**

     字段 | 类型 | 说明 |
    --- | --- | --- |
     requestId | String | 抄送事件的唯一标识。 |
     eventType | String | 事件类型，固定为 `USER_VIDEO_OFF`。 |
     timestamp | Number | 事件发生或抄送的时间戳，单位为毫秒。 |
     body | JSON | 消息体。 |
      roomArchiveId | String | 房间归档 ID，NERoom 房间组件会保证全局唯一，最大长度为 36 个字符。 |
      roomUuid | String | 房间标识，由您传入，NERoom 房间组件不保证全局唯一，您可自行保证 ID 唯一性，最大长度为 64 字符。 |
      userUuid | String | 用户标识。 |

- **示例**

    ```JSON
    {
        "requestId":"a0b855ceb96649f79ec967dc55209fea",
        "eventType":"USER_VIDEO_OFF",
        "timestamp":1648007048918,
        "body":{
            "roomArchiveId":"2331",
            "roomUuid":"12345",
            "userUuid":"someone",
        }
    }
    ```

## 成员上麦位

- **消息体**

     字段 | 类型 | 说明 |
    --- | --- | --- |
     requestId | String | 抄送事件的唯一标识。 |
     eventType | String | 事件类型，固定为 `USER_ON_SEAT`。 |
     timestamp | Number | 事件发生或抄送的时间戳，单位为毫秒。 |
     body | JSON | 消息体。 |
      room_archive_id | String | 房间归档 ID，NERoom 房间组件会保证全局唯一，最大长度为 36 个字符。 |
      room_uuid | String | 房间标识，由您传入，NERoom 房间组件不保证全局唯一，您可自行保证 ID 唯一性，最大长度为 64 字符。 |
      user_uuid | String | 用户标识。 |
      index | Integer | 麦位序号。 |

- **示例**

    ```JSON
    {
        "requestId":"a0b855ceb96649f79ec967dc55209fea",
        "eventType":"USER_ON_SEAT",
        "timestamp":1648007048918,
        "body":{
            "room_archive_id":"2331",
            "room_uuid":"12345",
            "user_uuid":"someone",
            "index":1
        }
    }
    ```

## 成员下麦位

- **消息体**

     字段 | 类型 | 说明 |
    --- | --- | --- |
     requestId | String | 抄送事件的唯一标识。 |
     eventType | String | 事件类型，固定为 `USER_OFF_SEAT`。 |
     timestamp | Number | 事件发生或抄送的时间戳，单位为毫秒。 |
     body | JSON | 消息体。 |
      room_archive_id | String | 房间归档 ID，NERoom 房间组件会保证全局唯一，最大长度为 36 个字符。 |
      room_uuid | String | 房间标识，由您传入，NERoom 房间组件不保证全局唯一，您可自行保证 ID 唯一性，最大长度为 64 字符。 |
      user_uuid | String | 用户标识。 |
      index | Integer | 麦位序号。 |

- **示例**

    ```JSON
    {
        "requestId":"a0b855ceb96649f79ec967dc55209fea",
        "eventType":"USER_OFF_SEAT",
        "timestamp":1648007048918,
        "body":{
            "room_archive_id":"2331",
            "room_uuid":"12345",
            "user_uuid":"someone",
            "index":1
        }
    }
    ```