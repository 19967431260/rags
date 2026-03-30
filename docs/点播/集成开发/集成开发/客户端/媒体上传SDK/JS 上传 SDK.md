JavaScript-SDK 是用于浏览器端点播上传的软件开发工具包，提供简单、便捷的方法，方便用户开发上传视频或图片文件的功能。

## <span id="功能特性">功能特性</span>

- 文件上传。
- 断点续传。
- 多文件状态管理。

## 示例代码

- [JavaScript 示例代码](https://github.com/netease-im/G2-API-Examples/tree/main/vod-upload/web/SampleCode-js)

- [React 示例代码](https://github.com/netease-im/G2-API-Examples/tree/main/vod-upload/web/SampleCode-React)

## 实现方法

### 1. 引入 SDK

文件上传依赖 `md5.js` 加密库，因此您需要提前引入 JS 文件：

```JavaScript
<script type="text/javascript" src="https://blueimp.github.io/JavaScript-MD5/js/md5.js"></script>
<script type="text/javascript" src="https://yx-web-nosdn.netease.im/sdk-release/upload_1.2.0.js"></script>
```

### 2. 初始化设置

关联文件选择输入框和上传按钮元素 ID，作为配置项参数传入 Uploader：

```JavaScript
var opt = {
    fileInputId: 'fileInput',
    fileUploadId: 'fileUploadBtn',
    getCheckSum: function(){ //获取鉴权信息
        return { AppKey, Nonce, CurTime, CheckSum }
    }
}
```

**其他配置项说明：**

- `trunkSize`：分片大小，最大 4MB。
- `fileExts`：允许上传的文件类型后缀列表（字符串数组）。
- `getInitInfo`：获取初始化信息，包括桶名、对象名、token 等。
- `onError`：错误处理函数。
- `onProgress`：上传进度回调处理函数。
- `onUploaded`：单文件上传成功的回调函数。
- `onAllUploaded`：全部文件上传成功的回调函数。
- `onAdd`：文件添加成功的回调函数。
- `noUploadFn`：无文件上传时的处理函数。
- `exsitFn`：文件已存在（待上传）列表中的处理函数。
- `mismatchFn`：文件格式不匹配的处理函数。

具体描述参考 **[配置项 API](#config)**。

### 3. 初始化

确定配置参数后，通过以下调用进行事件的绑定和相关初始化操作：

```JavaScript
<script type="text/javascript">
    const uploader = new Uploader(opt)
    uploader.init()
</script>
```

### 4. 上传文件

完成上述步骤后，即完成所有的上传接口调用。当用户选择上传文件后，将通过相关事件完成文件的上传。

### 5. 断点续传

当文件上传中断后，用户只需重新选择文件提交即可恢复上传（可自定义文件队列和状态管理）。

## <span id="config">配置项 API</span>

### <span id="getCheckSum">getCheckSum</span>

示例代码请参考 [upload.js](https://yx-web-nosdn.netease.im/sdk-release/upload_1.2.0.js) 中的描述。

该方法需要返回以下数据：

- **`AppKey`**：开发者平台分配的 appkey。
- **`Nonce`**：随机数（随机数，最大长度 128 个字符）。
- **`CurTime`**：当前 UTC 时间戳，从 1970 年 1 月 1 日 0 点 0 分 0 秒开始到现在的秒数。
- **`CheckSum`**：服务器认证需要，格式为 `SHA1(AppSecret+Nonce+CurTime)`，16 进制字符小写。计算 CheckSum 的示例代码请参考 [接口鉴权](https://doc.yunxin.163.com/vod/server-apis/TU3MzkwNDk?platform=server#%E6%8E%A5%E5%8F%A3%E9%89%B4%E6%9D%83)。

### <span id="onError">onError</span>

<style>
table th:first-of-type {
    width: 25%;
}
table th:nth-of-type(2) {
    width: 20%;
}
table th:nth-of-type(3) {
    width: 55%;
}
</style>

**参数**

名称 | 类型 | 说明
:---- | :---- | :----
errObj | Object | 带 errCode 和 errMsg 的 Object 或 XHR 错误对象。

**返回值**

无。

### <span id="onProgress">onProgress</span>

**参数**

名称 | 类型 | 说明
:---- | :---- | :----
curFile | Object | 文件对象。

**返回值**

无。

### <span id="onUploaded">onUploaded</span>

**参数**

名称 | 类型 | 说明
:---- | :---- | :----
curFile | Object | 文件对象。

**返回值**

无。

### <span id="onAllUploaded">onAllUploaded</span>

**参数**

无。

**返回值**

无。

### <span id="onAdd">onAdd</span>

**参数**

名称 | 类型 | 说明
:---- | :---- | :----
curFile | Object | 文件对象

**返回值**

无。

### <span id="noUploadFn">noUploadFn</span>

**参数**

无。

**返回值**

无。

### <span id="existFn">existFn</span>

**参数**

无。

**返回值**

无。

### <span id="mismatchFn">mismatchFn</span>

**参数**

无。

**返回值**

无。

## <span id="版本更新记录">版本更新记录</span>

1.2.0 (2025-01-13)

支持批量上传。

1.1.0 (2023-03-23)

增加文件类型限制。

1.0.0 (2021-07-22)

JavaScript-SDK 初始版本，提供文件上传的基本功能，包括：文件上传、断点续传等。