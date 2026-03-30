NERoom 支持配置回调来接收某些重要事件。当事件被触发时，回调服务将主动推送相应事件内容到用户配置的回调地址。本文介绍 NERoom 事件的参数说明和示例。


::: note note
开通消息抄送的操作步骤请参考[开通消息抄送](https://doc.yunxin.163.com/meeting/server-apis/DY0OTgxODU)。
:::

## 创建及关闭房间
* 消息体
字段名 | 类型 | 描述
---- | -------------- | ---------
requestId | String | 抄送事件唯一标识 |
eventType | String | 事件类型<br>创建房间：CREATE_ROOM<br>关闭房间：CLOSE_ROOM|
timestamp | Number | 该事件发生的 UTC 时间戳，从 1970 年 1 月 1 日 0 点 0 分0 秒开始到现在的毫秒数 |
body | Json | 消息体 |

body字段如下：

字段名 | 类型 | 描述
---- | -------------- | ---------
roomArchiveId | String | 归档到历史记录中的房间 ID，全局唯一，最大长度36个字符 |
roomUuid | String | 房间标识，应用内进行中的房间唯一编号，最大长度64个字符|
operatorUserUuid | Number | 操作人的用户标识 |

* 示例

```java
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

* 消息体
字段名 | 类型 | 描述
---- | -------------- | ---------
requestId | String | 抄送事件唯一标识 |
eventType | String | 事件类型<br>加入房间：USER_JOIN_ROOM  <br>离开房间：USER_LEAVE_ROOM|
timestamp | Number | 该事件发生的 UTC 时间戳，从 1970 年 1 月 1 日 0 点 0 分0 秒开始到现在的毫秒数 |
body | Json | 消息体 |

body字段如下：

字段名 | 类型 | 描述
---- | -------------- | ---------
roomArchiveId | String | 归档到历史记录中的房间 ID，全局唯一，最大长度36个字符 |
roomUuid | String | 房间标识，应用内进行中的房间唯一编号，最大长度64个字符|
users | 数组 | 用户信息 |
users.role | String | 用户角色 |
users.userUuid | String | 用户标识 |

* 示例

```java
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

## 成员角色表变更

* 消息体
字段名 | 类型 | 描述
---- | -------------- | ---------
requestId | String | 抄送事件唯一标识 |
eventType | String | 事件类型，固定   USER_ROLE_CHANGE|
timestamp | Number | 该事件发生的 UTC 时间戳，从 1970 年 1 月 1 日 0 点 0 分0 秒开始到现在的毫秒数 |
body | Json | 消息体 |

body字段如下：

字段名 | 类型 | 描述
---- | -------------- | ---------
roomArchiveId | String | 归档到历史记录中的房间 ID，全局唯一，最大长度36个字符 |
roomUuid | String | 房间标识，应用内进行中的房间唯一编号，最大长度64个字符|
userUuid | String | 被修改用户的标识 |
oldRole | String | 修改前用户角色 |
newRole | String | 修改后用户角色 |
operatorUserUuid | String | 操作人的用户标识 |

* 示例

```java
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

* 消息体
字段名 | 类型 | 描述
---- | -------------- | ---------
requestId | String | 抄送事件唯一标识 |
eventType | String | 事件类型，固定   USER_NAME_CHANGE|
timestamp | Number | 该事件发生的 UTC 时间戳，从 1970 年 1 月 1 日 0 点 0 分0 秒开始到现在的毫秒数 |
body | Json | 消息体 |

body字段如下：

字段名 | 类型 | 描述
---- | -------------- | ---------
roomArchiveId | String | 归档到历史记录中的房间 ID，全局唯一，最大长度36个字符 |
roomUuid | String | 房间标识，应用内进行中的房间唯一编号，最大长度64个字符|
userUuid | String | 被修改用户的标识 |
oldUserName | String | 修改前用户名字 |
newUserName | String | 修改后用户名字 |
operatorUserUuid | String | 操作人的用户标识 |

* 示例

```java
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

当录制文件生成完毕，并且上传到点播系统成功后发出本次回调

* 消息体
字段名 | 类型 | 描述
---- | -------------- | ---------
requestId | String | 抄送事件唯一标识 |
eventType | String | 事件类型，固定   RTC_RECORD|
timestamp | Number | 该事件发生的 UTC 时间戳，从 1970 年 1 月 1 日 0 点 0 分0 秒开始到现在的毫秒数 |
body | Json | 消息体 |

body字段如下：

字段名 | 类型 | 描述
---- | -------------- | ---------
roomArchiveId | String | 归档到历史记录中的房间 ID，全局唯一，最大长度36个字符 |
roomUuid | String | 房间标识，应用内进行中的房间唯一编号，最大长度64个字符|
userUuid | String | 录制的用户 ID 标识<note type="notice">单人录制（`mix` 字段为 false）时，此字段才有效；混录（`mix` 字段为 true）时，此字段为空。</note> |
type | String | 文件的类型，即文件扩展名。包括：<br>aac：实时音频录制文件。<br>mp4：实时视频录制文件。<br>flv：互动直播视频录制文件 |
mix | Boolean | 是否为混合录制文件。<br>true：混合录制文件。<br>false：单人录制文件 |
filename | String | 文件名，直接存储，混合录制文件 filename 带有"-mix"标记|
md5 | String | 文件的 MD5 值|
url | String | 文件的下载地址|
size|Number|文件大小，单位为字节|
vid|Number|点播文件 ID，通过该参数可以调用点播接口查询相关信息。|
pieceIndex|Number|录制文件的切片索引，如果单通通话录制时长超过切片时长，则录制文件会被且被切割成多个文件|
timestamp|Number|录制文件生成的 UTC 时间戳。单位：毫秒|

* 示例

```java
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

当白板录制文件生成完毕，并且上传到点播系统成功后发出本次回调

* 消息体
字段名 | 类型 | 描述
---- | -------------- | ---------
requestId | String | 抄送事件唯一标识 |
eventType | String | 事件类型，固定   WHITEBOARD_RECORD|
timestamp | Number | 该事件发生的 UTC 时间戳，从 1970 年 1 月 1 日 0 点 0 分0 秒开始到现在的毫秒数 |
body | Json | 消息体 |

body字段如下：

字段名 | 类型 | 描述
---- | -------------- | ---------
roomArchiveId | String | 归档到历史记录中的房间 ID，全局唯一，最大长度36个字符 |
roomUuid | String | 房间标识，应用内进行中的房间唯一编号，最大长度64个字符|
filename | String | 文件名 |
md5 | String | 文件的 MD5 值|
size| Number|文件大小，单位为字节|
url|String|文件的下载地址|
recordTime| Number|录制时间戳，单位：毫秒|
timestamp| Number|录制文件生成的系统时间戳，单位：毫秒|

* 示例

```java
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


  