通过该接口创建一个 RTC 用户账号（`uid`），账号可用于音视频应用在用户加入房间时的安全检测场景。

## 请求信息

### 请求 URI

```
POST https://{endpoint}/neroom/v4/rtc_uid
```

{endpoint} 为房间组件接入地址的域名，默认为 `roomkit.yunxinapi.com`。如果您的应用主要服务于海外用户，请将域名设置为海外数据中心域名（`roomkit-sg.yunxinapi.com`）。

### 请求头参数

请求 Header 的设置请参考 <a href="https://doc.yunxin.163.com/neroom/docs/TMyMDg2Mzg?platform=server" target="_blank">请求结构</a>。

### 请求示例

```
POST https://roomkit.yunxinapi.com/neroom/v4/rtc_uid
```

## 响应信息

### 响应体参数

| 参数名称 | 类型 | 示例 | 说明 |
| ---- | ---- | ---- | ---- |
| code | int | 0 | 状态码，0 表示成功，具体请参考 [错误码](https://doc.yunxin.163.com/neroom/server-apis/TI3ODc2MTc?platform=server)。 |
| msg | String | Operation succeeded. | 业务结果描述。 |
| ts | Long | 1648021056815 | NERoom 服务器处理该请求的完成时间。<br>该时间为 Unix 时间戳，即从 1970 年 1 月 1 日 0 点 0 分 0 秒开始到现在的毫秒数。 |
| request_id | String | 7c4b***e3a4d995 | 请求的唯一标识。 |
| cost | String | 48ms | 处理该请求所消耗的时间。 |
| data | JsonObject     | - | `rtcUid` 信息。 |
   uid | Long | 1100 | `rtcUid`，指 RTC 用户 ID，可用于网易易盾音视频应用在用户加入房间时的安全检测场景，详情请参考《网易易盾》文档 [接口调用概述](https://support.dun.163.com/documents/594247746924453888?docId=600827338598789120#%E4%BA%91%E4%BF%A1) 云信章节。 |

### 响应体示例

```JSON
{
  "code": 0,
  "msg": "Operation succeeded.",
  "ts": 1691410833636,
  "cost": "318ms",
  "request_id": "local_a7e68aa2d1ee46e1be0f239d1f352773",
  "data":
    {
      "uid": 1100
    }
}
```