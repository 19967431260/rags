## <span id="NOS云存储服务">NOS云存储服务</span>

SDK提供远程文件存储功能，用户通过SDK提供的接口可以实现文件的上传和下载。

### 配置文件标签信息

将文件上传到NOS服务器时可以指定文件标签和过期时间，过期时间最少为1天。在SDK初始化完成后或者在进行文件上传前调用该接口配置标签信息。

- API原型

```csharp
/// <summary>
/// 对上传资源时使用的各场景资源生命周期进行初始化，开发者最多可自定义10个场景，
/// 并指定场景资源的生命周期，并可以对缺省场景（"nim_default_im"、"nim_default_profile_icon"）进行覆盖（重新指定生命周期）
/// </summary>
public static void InitNosTags(System.Collections.Generic.List<NosTagInfo> tags)
```

### 下载

#### 通过URL下载文件

- API原型

```csharp
/// <summary>
/// 下载资源
/// </summary>
/// <param name="nosUrl">下载资源的URL</param>
/// <param name="resHandler">下载的结果回调</param>
/// <param name="prgHandler">下载进度的回调</param>
/// <param name="userData">传入到下载进度回调中的用户数据</param>
public static void Download(string nosUrl, DownloadResultHandler resHandler, ProgressResultHandler prgHandler, object userData = null)
```

- 示例

```csharp
NIM.Nos.NosAPI.Download("NOSURL", OnDownloadCompleted, DwonloadProgressCallback);

private void OnDownloadCompleted(int rescode, string filePath, string callId, string resId)
{
    if(rescode == 200)
    {
        //文件下载成功，filePath 为文件保存路径
    }
    else
    {
        //文件下载失败
    }
}

private void DwonloadProgressCallback(ProgressData prgData)
{
    //下载进度回调
    //prgData.CurrentSize:当前已下载文件大小
    //prgData.TotalSize:文件总大小
}
```

#### 下载消息中的文件

- API原型

```csharp
/// <summary>
/// 获取资源
/// </summary>
/// <param name="msg">消息体,NIMVideoMessage NIMAudioMessage NIMFileMessage等带msg_attach属性的有下载信息的消息</param>
/// <param name="resHandler">下载的结果回调</param>
/// <param name="prgHandler">下载进度的回调</param>
public static void DownloadMedia(NIMIMMessage msg, DownloadResultHandler resHandler, ProgressResultHandler prgHandler, object userData = null)
```

- 示例

```csharp
NosAPI.DownloadMedia (msg, (rescode, filePath, callId, resId)=>
        {

            UnityEngin.Debug.Log(string.Format("rescode:{0},filepath:{1},callId:{2},resId:{3}",rescode,filePath,callId, resId));
        },
        (prgData)=>
        {
            UnityEngin.Debug.Log(string.Format("curr:{0},total:{1},{2}",prgData.CurrentSize,prgData.TotalSize,prgData.FilePath));
        });
```

### 上传

- API原型

```csharp
/// <summary>
/// 上传资源
/// </summary>
/// <param name="localFile">本地文件的完整路径</param>
/// <param name="resHandler">上传的结果回调</param>
/// <param name="prgHandler">上传进度的回调</param>
public static void Upload(string localFile, UploadResultHandler resHandler, ProgressResultHandler prgHandler, object userData = null)
```

- 示例

```csharp
NIM.Nos.NosAPI.Upload("FILE PATH", FileUploadCallback, ProgressCallback);
private void FileUploadCallback(int rescode, string url)
{
    if (rescode == 200)
    {
        //上传成功，url为NOS存储中文件的下载URL
    }
    else
    {
        //上传失败
    }
}

private void ProgressCallback(ProgressData prgData)
{
    //上传进度回调
    //prgData.CurrentSize:当前已上传文件大小
    //prgData.TotalSize:文件总大小
}

```

### 使用指定标签上传

标签需要使用`InitNosTags`进行配置，使用未初始化的标签不会进行文件上传。

- API原型

```csharp
/// <summary>
/// 上传资源
/// </summary>
/// <param name="localFile">本地文件的完整路径</param>
/// <param name="tag">场景标签，主要用于确定文件的保存时间</param>
/// <param name="resHandler">上传的结果回调</param>
/// <param name="prgHandler">上传进度的回调</param>
public static void Upload2(string localFile, string tag, UploadResultHandler resHandler, ProgressResultHandler prgHandler, object userData = null)
```

### 注册默认下载回调

在接收到包含文件的消息后SDK会自动下载文件，注册下载回调能够获取到文件的下载进度和结果，在自动下载失败时用户可以手动调用下载接口再次尝试下载。

- API原型

```csharp
/// <summary>
/// 注册下载回调，通过注册回调获得http下载结果通知，刷新资源
/// </summary>
/// <param name="handler">下载的结果回调</param>
/// 
public static void RegDownloadCb(DownloadResultHandler handler)
```

### 注册默认上传回调

发送包含文件的消息时SDK会自动将文件上传到NOS服务器，上传成功后将文件的下载URL发送给接收方，注册上传回调可以获取到文件的上传信息。

- API原型

```csharp
/// <summary>
/// (全局回调)注册上传回调，通过注册回调获得HTTP上传结果通知（所有触发HTTP上传任务的接口的参数列表里无法设置通知回调处理函数的通知都走这个通知，比如发送文件图片语音消息等）
/// </summary>
/// <param name="callback"></param>
/// <param name="data"></param>
public static void RegisterDefaultUploadCallback(UploadCb callback, IntPtr data)
```