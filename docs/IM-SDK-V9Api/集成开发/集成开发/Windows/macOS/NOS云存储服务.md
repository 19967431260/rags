 
### <span id="下载">下载</span>

下载资源，回调函数包括了下载结果以及下载进度

下载结果回调函数

```c
@param rescode：200表示下载成功
@param file_path：下载文件的完整路径
@param call_id：对话id
@param res_id：消息id，与对话id一起可定位到具体的消息，然后根据rescode调整UI呈现
typedef void(*nim_nos_download_cb_func)(int rescode, const char *file_path, const char *call_id, const char *res_id, const char *json_extension, const void *user_data);
```

下载进度回调函数

```c
@param downloaded_size：已下载大小
@param file_size：文件大小，单位都是字节
typedef void(*nim_nos_download_prg_cb_func)(__int64 downloaded_size, __int64 file_size, const char *json_extension, const void *user_data);
```

示例代码如下：

C++

```c++
void DownloadResourceCallback(nim::NIMResCode res_code, const std::string& file_path, const std::string& call_id, const std::string& res_id)
{

}

void DownloadResourceProgressCallback(__int64 downloaded_size, __int64 file_size)
{

}

void foo(const IMMessage& msg)
{
	nim::NOS::FetchMedia(msg, &DownloadResourceCallback, &DownloadResourceProgressCallback);
}
```

C#

```c#
void foo(NIM.NIMIMMessage message)
{
	NIM.Nos.NosAPI.DownloadMedia(message, (rescode, filePath, callId, resId) =>
	{
		if (rescode == 200)
		{
			
		}
	},
	(prgData) =>
	{
		
	});
}
```

C

```c
void CallbackDownload(int res_code, const char *file_path, const char *call_id, const char *res_id, const char *json_extension, const void *user_data)
{
	···
}

void CallbackProgress(__int64 completed_size, __int64 total_size, const char *json_extension, const void *callback)
{
	···
}

typedef void(*nim_nos_download_media)(const char *json_msg, nim_nos_download_cb_func callback_result, const void *download_user_data, nim_nos_download_prg_cb_func prg_cb, const void *prg_user_data);

void foo(const IMMessage& msg)
{
	nim_nos_download_media func = (nim_nos_download_media) GetProcAddress(hInst, "nim_nos_download_media");
	func(msg.ToJsonString(false).c_str(), &CallbackDownload, nullptr, &CallbackProgress, nullptr);
}
```

### <span id="下载与暂停">下载与暂停</span>

从3.3.0开始SDK新增了下载的扩展类接口，支持断点续传，开发者可以通过该接口设置自定义的超时时间，下载文件的本地存放路径，以及获取下载瞬时速度、下载平均速度等信息。

C++

```c++
//下载结果回调
void CallbackDownload(nim::NIMResCode res_code, const nim::DownloadMediaResult& result)
{
	if (res_code == kNIMResSuccess)
	{
		//下载成功
	}
	else if (res_code == kNIMLocalResMsgNosDownloadCancel)
	{
		//下载暂停
	}
	else
	{
		//下载失败
	}
}

//下载过程回调，参数：当前已下载文件大小， 文件大小， 下载相关信息
void CallbackHttpPro(__int64 completed_size, __int64 file_size, const ProgressData& data)
{
	...
}

//下载瞬时速度回调
void CallbackSpeed(__int64 speed)
{
	if (speed > 0)
	{
		char res[1024];
		sprintf_s(res, "speed : %lld B/s(%lf KB/s)", speed, (static_cast<double>(speed))/1024);
	}
}

static __int64 actual_size_ = 0;
//下载结束后信息回调，参数：此次下载文件的大小， 平均速度
void CallbackTransferInfo(__int64 actual_size, __int64 speed)
{	
	actual_size_ += actual_size;
	char res[1024];
	sprintf_s(res, "average speed : %lld(%lf KB/s)", speed, (static_cast<double>(speed))/1024);

	sprintf_s(res, "actual size : %lld, block size : %lld", actual_size_, actual_size);
}

//发起下载任务
void foo_start_http_download(const std::string& task_uuid)
{
	Json::FastWriter writer;
	Json::Value value;
	value[kNIMNosLowLimit] = ; //int(选填) HTTP通用配置，传输速度，每秒字节数（默认10）
	value[kNIMNosLowTime] = ;  //int(选填) HTTP通用配置，传输过程中当low_time秒时间内传输速度小于low_limit时(字节每秒)，下载任务会返回超时而取消（默认60）
	value[kNIMNosTimeout] = ;  //int(选填) HTTP通用配置，超时时间，单位ms，下载时最小10000，上传时最小30000，不设置默认30000
	value[kNIMNosSaveAsFilePath] = ; //string(选填) HTTP下载任务的文件存放本地路径，不填则默认路径回调中返回
	value[kNIMNosFileSize] = ; //int64(断点续传必填) HTTP下载任务的文件大小，需要续传功能必填，单位Byte
	value[kNIMNosTaskId] = task_uuid;   //string(断点续传必填) HTTP通用配置，任务ID，如果传入的ID是曾经未完成的传输任务，则会开始续传（用户需要保证ID的唯一性）
	nim::NOS::DownloadResourceEx(url, writer.write(value), &CallbackDownload, &CallbackHttpPro, &CallbackSpeed, &CallbackTransferInfo);
}

//暂停下载任务
void foo_pause_http_download(const std::string& task_uuid)
{
	nim::NOS::StopDownloadResourceEx(task_uuid);
}
```

C#

```c#
//发起下载任务
private void StartDownloadEx()
{
	//设置下载控制属性
	HttpExtendedParameters params = new HttpExtendedParameters();
	NosAPI.DownloadEx(NosUploadData.Url,params, ReportDownloadResult, IntPtr.Zero,
		ReportDownloadPrg, IntPtr.Zero,
		ReportDownloadSpeed, IntPtr.Zero,
		ReportDownloadInfo, IntPtr.Zero);
}

private void ReportDownloadInfo(long actual_download_size, long download_speed, string json_extension, IntPtr user_data)
{
	//TODO:下载信息
}

private void ReportDownloadSpeed(long download_speed, string json_extension, IntPtr user_data)
{
	//TODO:下载速度
}

private void ReportDownloadPrg(long downloaded_size, long file_size, string json_extension, IntPtr user_data)
{
	//TODO:下载进度
}

private void ReportDownloadResult(int rescode, string file_path, string call_id, string res_id, string json_extension, IntPtr user_data)
{
	//TODO：下载结果
}

//停止下载任务,taskId 为调用DownloadEx 时传入的参数，参考 HttpExtendedParameters
NIM.Nos.NosAPI.StopDownloadEx(string taskId, string ext = null)
```

C

```c
//下载结果回调
static void CallbackDownloadEx(int res_code, const char *file_path, const char *call_id, const char *res_id, const char *json_extension, const void *user_data)
{
	if (res_code == kNIMResSuccess)
	{
		//下载成功
	}
	else if (res_code == kNIMLocalResMsgNosDownloadCancel)
	{
		//下载暂停
	}
	else
	{
		//下载失败
	}
}

//下载过程回调，参数：当前已下载文件大小， 文件大小， 下载相关信息
static void CallbackProgressEx(int64_t completed_size, int64_t total_size, const char *json_extension, const void *callback)
{
	···
}

//下载瞬时速度回调
static void CallbackSpeed(int64_t speed, const char *json_extension, const void *callback)
{
	if (speed > 0)
	{
		char res[1024];
		sprintf_s(res, "speed : %lld B/s(%lf KB/s)", speed, (static_cast<double>(speed))/1024);
	}
}

static __int64 actual_size_ = 0;
//下载结束后信息回调，参数：此次下载文件的大小， 平均速度
static void CallbackTransferInfo(int64_t actual_size, int64_t speed, const char *json_extension, const void *callback)
{
	actual_size_ += actual_size;
	char res[1024];
	sprintf_s(res, "average speed : %lld(%lf KB/s)", speed, (static_cast<double>(speed))/1024);

	sprintf_s(res, "actual size : %lld, block size : %lld", actual_size_, actual_size);
}

typedef void(*nim_nos_download_ex)(const char *nos_url, const char *json_extension, nim_nos_download_cb_func callback_result, const void *res_user_data, nim_nos_download_prg_cb_func prg_cb, const void *prg_user_data, nim_nos_download_speed_cb_func speed_cb, const void *speed_user_data, nim_nos_download_info_cb_func info_cb, const void *info_user_data);

typedef void(*nim_nos_stop_download_ex)(const char *task_id, const char *json_extension);

//发起下载任务
void foo_start_http_download(const std::string& task_uuid)
{
	Json::FastWriter writer;
	Json::Value value;
	value[kNIMNosLowLimit] = ; //int(选填) HTTP通用配置，传输速度，每秒字节数（默认10）
	value[kNIMNosLowTime] = ;  //int(选填) HTTP通用配置，传输过程中当low_time秒时间内传输速度小于low_limit时(字节每秒)，下载任务会返回超时而取消（默认60）
	value[kNIMNosTimeout] = ;  //int(选填) HTTP通用配置，超时时间，单位ms，下载时最小10000，上传时最小30000，不设置默认30000
	value[kNIMNosSaveAsFilePath] = ; //string(选填) HTTP下载任务的文件存放本地路径，不填则默认路径回调中返回
	value[kNIMNosFileSize] = ; //int64(断点续传必填) HTTP下载任务的文件大小，需要续传功能必填，单位Byte
	value[kNIMNosTaskId] = task_uuid;   //string(断点续传必填) HTTP通用配置，任务ID，如果传入的ID是曾经未完成的传输任务，则会开始续传（用户需要保证ID的唯一性）

	nim_nos_download_ex func = (nim_nos_download_ex) GetProcAddress(hInst, "nim_nos_download_ex");
	func(nos_url.c_str(), writer.write(value).c_str(), &CallbackDownloadEx, callback_result_userdata, &CallbackProgressEx, callback_progress_pointer, &CallbackSpeed, callback_speed_pointer, &CallbackTransferInfo, callback_transfer_pointer);
}	

//暂停下载任务
void foo_pause_http_download(const std::string& task_uuid)
{
	nim_nos_stop_download_ex func = (nim_nos_stop_download_ex) GetProcAddress(hInst, "nim_nos_stop_download_ex");
	func(task_uuid.c_str(), nullptr);
}
```

### <span id="上传">上传</span>

上传资源，回调函数包括了上传结果以及上传进度

上传结果回调函数

```c
@param rescode：错误码，200表示成功
@param url：上传成功后返回的url
typedef void(*nim_nos_upload_cb_func)(int rescode, const char *url, const char *json_extension, const void *user_data);
```

上传进度回调函数

```c
@uploaded_size：已上传大小
@file_size：文件大小
typedef void(*nim_nos_upload_prg_cb_func)(__int64 uploaded_size, __int64 file_size, const char *json_extension, const void *user_data);	
```

示例代码如下：

C++

```c++
void OnUploadCallback(int res_code, const std::string& url)
{

}

void foo()
{
	nim::NOS::UploadResource("D://test_file.txt", &OnUploadCallback);
}
```

C#

```c#
void foo()
{
	NIM.Nos.NosAPI.Upload("D://test_file.txt", (res_code, url) =>
	{
	}, null);
}
```

C

```c
void CallbackUpload(int res_code, const char *url, const char *json_extension, const void *user_data)
{
	···
}

void CallbackProgress(__int64 completed_size, __int64 total_size, const char *json_extension, const void *callback)
{
	···
}

typedef void(*nim_nos_upload)(const char *local_file, nim_nos_upload_cb_func callback_result, const void *res_user_data, nim_nos_upload_prg_cb_func prg_cb, const void *prg_user_data);

void foo()
{
	nim_nos_upload func = (nim_nos_upload) GetProcAddress(hInst, "nim_nos_upload");
	func("D://test_file.txt", &CallbackUpload, nullptr, &CallbackProgress, nullptr);
}
```

### <span id="上传与暂停">上传与暂停</span>

从3.3.0开始SDK新增了上传的扩展类接口，支持断点续传，开发者可以通过该接口设置自定义的超时时间，以及获取上传瞬时速度、上传平均速度等信息。

C++

```c++
//上传结果回调
void CallbackUpload(nim::NIMResCode res_code, const nim::DownloadMediaResult& result)
{
	if (res_code == kNIMResSuccess)
	{
		//上传成功
	}
	else if (res_code == kNIMLocalResMsgNosUploadCancel)
	{
		//上传暂停
	}
	else
	{
		//上传失败
	}
}

//上传过程回调，参数：当前已上传文件大小， 文件大小， 上传相关信息
void CallbackHttpPro(__int64 completed_size, __int64 file_size, const ProgressData& data)
{
	...
}

//上传瞬时速度回调
void CallbackSpeed(__int64 speed)
{
	if (speed > 0)
	{
		char res[1024];
		sprintf_s(res, "speed : %lld B/s(%lf KB/s)", speed, (static_cast<double>(speed))/1024);
	}
}

static __int64 actual_size_ = 0;
//上传结束后信息回调，参数：此次上传文件的大小， 平均速度
void CallbackTransferInfo(__int64 actual_size, __int64 speed)
{	
	actual_size_ += actual_size;
	char res[1024];
	sprintf_s(res, "average speed : %lld(%lf KB/s)", speed, (static_cast<double>(speed))/1024);

	sprintf_s(res, "actual size : %lld, block size : %lld", actual_size_, actual_size);
}

//发起上传任务
void foo_start_http_upload(const std::string& task_uuid)
{
	Json::FastWriter writer;
	Json::Value value;
	value[kNIMNosLowLimit] = ; //int(选填) HTTP通用配置，传输速度，每秒字节数（默认10）
	value[kNIMNosLowTime] = ;  //int(选填) HTTP通用配置，传输过程中当low_time秒时间内传输速度小于low_limit时(字节每秒)，下载任务会返回超时而取消（默认60）
	value[kNIMNosTimeout] = ;  //int(选填) HTTP通用配置，超时时间，单位ms，下载时最小10000，上传时最小30000，不设置默认30000
	value[kNIMNosNeedContinueTrans] = ; //bool 需要支持断点续传True
	value[kNIMNosTaskId] = task_uuid;   //string(断点续传必填) HTTP通用配置，任务ID，如果传入的ID是曾经未完成的传输任务，则会开始续传（用户需要保证ID的唯一性）
	nim::NOS::UploadResourceEx(file_path, writer.write(value), &CallbackUpload, &CallbackHttpPro, &CallbackSpeed, &CallbackTransferInfo);
}

//暂停上传任务
void foo_pause_http_upload(const std::string& task_uuid)
{
	nim::NOS::StopUploadResourceEx(task_uuid);
}
```

C#

```c#
//开始上传任务
private void StartUploadEx(string filePath)
{
	HttpExtendedParameters params = new HttpExtendedParameters();
	params.TaskID = ""; //任务ID，停止上传任务时需要用到该值
	NIM.Nos.NosAPI.UploadEx(filePath,params, ResultCb, Marshal.StringToHGlobalAnsi("UploadResult"),
	ReportPrg, Marshal.StringToHGlobalAnsi("UploadProgress"),
	ReportSpeed, Marshal.StringToHGlobalAnsi("UploadSpeed"),
	ReportInfo, Marshal.StringToHGlobalAnsi("UploadInfo"));
}

private void ReportInfo(long actual_upload_size, long upload_speed, string json_extension, IntPtr user_data)
{
	//TODO:上传信息
}

private void ReportPrg(long uploaded_size, long file_size, string json_extension, IntPtr user_data)
{
	//TODO:上传进度	
}

private void ReportSpeed(long upload_speed, string json_extension, IntPtr user_data)
{
	//TODO:上传速度
}

private void ResultCb(int rescode, string url, string json_extension, IntPtr user_data)
{
	//TODO:上传结果
}

//停止上传,taskId 为调用 UploadEx 时传入的参数，参考 HttpExtendedParameters
NIM.Nos.NosAPI.StopUploadEx(string taskId, string ext = null)
```

C

```c
//上传结果回调
static void CallbackUploadEx(int res_code, const char *url, const char *json_extension, const void *user_data)
{
	if (res_code == kNIMResSuccess)
	{
		//下载成功
	}
	else if (res_code == kNIMLocalResMsgNosDownloadCancel)
	{
		//下载暂停
	}
	else
	{
		//下载失败
	}
}

//上传过程回调，参数：当前已上传文件大小， 文件大小， 上传相关信息
static void CallbackProgressEx(int64_t completed_size, int64_t total_size, const char *json_extension, const void *callback)
{
	···
}

//上传瞬时速度回调
static void CallbackSpeed(int64_t speed, const char *json_extension, const void *callback)
{
	if (speed > 0)
	{
		char res[1024];
		sprintf_s(res, "speed : %lld B/s(%lf KB/s)", speed, (static_cast<double>(speed))/1024);
	}
}

static __int64 actual_size_ = 0;
//上传结束后信息回调，参数：此次上传文件的大小， 平均速度
static void CallbackTransferInfo(int64_t actual_size, int64_t speed, const char *json_extension, const void *callback)
{
	actual_size_ += actual_size;
	char res[1024];
	sprintf_s(res, "average speed : %lld(%lf KB/s)", speed, (static_cast<double>(speed))/1024);

	sprintf_s(res, "actual size : %lld, block size : %lld", actual_size_, actual_size);
}

typedef void(*nim_nos_upload_ex)(const char *local_file, const char *json_extension, nim_nos_upload_cb_func callback_result, const void *res_user_data, nim_nos_upload_prg_cb_func prg_cb, const void *prg_user_data, nim_nos_upload_speed_cb_func speed_cb, const void *speed_user_data, nim_nos_upload_info_cb_func info_cb, const void *info_user_data);

typedef void(*nim_nos_stop_upload_ex)(const char *task_id, const char *json_extension);


//发起上传任务
void foo_start_http_download(const std::string& task_uuid)
{
	Json::FastWriter writer;
	Json::Value value;
	value[kNIMNosLowLimit] = ; //int(选填) HTTP通用配置，传输速度，每秒字节数（默认10）
	value[kNIMNosLowTime] = ;  //int(选填) HTTP通用配置，传输过程中当low_time秒时间内传输速度小于low_limit时(字节每秒)，下载任务会返回超时而取消（默认60）
	value[kNIMNosTimeout] = ;  //int(选填) HTTP通用配置，超时时间，单位ms，下载时最小10000，上传时最小30000，不设置默认30000
	value[kNIMNosNeedContinueTrans] = ; //bool 需要支持断点续传True
	value[kNIMNosTaskId] = task_uuid;   //string(断点续传必填) HTTP通用配置，任务ID，如果传入的ID是曾经未完成的传输任务，则会开始续传（用户需要保证ID的唯一性）

	nim_nos_upload_ex func = (nim_nos_upload_ex) GetProcAddress(hInst, "nim_nos_upload_ex");
	func(local_file.c_str(), writer.write(value).c_str(), &CallbackUploadEx, callback_result_userdata, &CallbackProgressEx, callback_progress_pointer, &CallbackSpeed, callback_speed_pointer, &CallbackTransferInfo, callback_transfer_pointer);
}	

//暂停上传任务
void foo_pause_http_download(const std::string& task_uuid)
{
	nim_nos_stop_upload_ex func = (nim_nos_stop_upload_ex) GetProcAddress(hInst, "nim_nos_stop_upload_ex");
	func(task_uuid.c_str(), nullptr);
}
```
