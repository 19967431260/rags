<!---keywords:短信接口，短信验证码接口，手机短信验证码接口，短信发送接口，php 短信接口，java 短信接口，短信验证码服务手机短信接口，，短信接口提供商--->
<!---description:网易云信 SMS 短信接口平台服务商，提供专业短信送达服务，包括验证码短信、通知短信、运营短信、语音验证码。--->

短信服务（Short Message Service）是网易云信为用户提供的一种通信服务能力。主要分为验证码短信、通知类短信和运营类短信，在调用短信验证码接口时可以同时调用校验验证码接口进行验证码校验。

本文详细介绍了短信接口请求格式、参数、示例代码以及错误码。

:::note note
- 短信服务属于收费功能，有关计费信息请参考 [计费概述](https://doc.yunxin.163.com/sms/concept/TMwMTQxNzU?platform=server) 或联系您的网易云信客户经理。
- 应用服务端调用短信 API 需遵循固定的请求结构和请求方式。详细规范请参考 [API 调用方式说明](https://doc.yunxin.163.com/messaging2/server-apis/zcwODA3MTU?platform=server)。
:::

<style>
table th:first-of-type {
    width: 15%;
}
table th:nth-of-type(2) {
    width: 15%;
}
table th:nth-of-type(3) {
    width: 15%;
}
table th:nth-of-type(4) {
    width: 55%;
}
</style>

## 发送短信验证码

向指定的手机号码发送文本短信验证码或语音短信验证码。

### 请求 URL

```
POST https://sms.yunxinapi.com/sms/sendcode.action HTTP/1.1
Content-Type:application/x-www-form-urlencoded;charset=utf-8
```

### 请求头

请求头的参数说明请参考 [请求头](https://doc.yunxin.163.com/messaging/server-apis/jk3MzY2MTI?platform=server#请求头参数)。

### 请求参数

:::::: div linked-codes
::: code 新版（2025/11/5）
<table><thead><tr> <th>参数</th><th>类型</th><th>是否必需</th><th>说明</th></tr></thead>
<tr> <td>mobile</td><td>String</td><td>是</td><td>目标手机号码，非中国大陆手机号码需要填写国家代码(如美国：+1-xxxxxxxxxx)或地区代码(如香港：+852-xxxxxxxx)</td></tr>
<tr> <td> templateid </td><td> Long </td><td>是</td><td>模板 ID，模板通过后可在模板列表页面获取。</td></tr>
<tr> <td> codeLen </td><td> int </td><td>否</td><td>验证码长度，默认为 4 位，取值范围为 4-10 （注：语音验证码的取值范围为 4-8 位）。</td></tr>
<tr> <td> paramMap </td><td> String </td><td>否</td><td>客户自定义验证码，长度为 4 ~ 10 位，支持字母和数字。如果设置了该参数，则 codeLen 参数无效。JSONObject 格式，例如：{"code":"1234"}</td></tr>
</table>
:::
::: code 旧版
<table><thead><tr> <th>参数</th><th>类型</th><th>是否必需</th><th>说明</th></tr></thead>
<tr> <td>mobile</td><td>String</td><td>是</td><td>目标手机号码，非中国大陆手机号码需要填写国家代码(如美国：+1-xxxxxxxxxx)或地区代码(如香港：+852-xxxxxxxx)</td></tr>
<tr> <td> templateid </td><td> int </td><td>否</td><td>模板编号(如不指定则使用配置的默认模板)</td></tr>
<tr> <td> codeLen </td><td> int </td><td>否</td><td>验证码长度，默认为 4 位，取值范围为 4-10 （注：语音验证码的取值范围为 4-8 位）。</td></tr>
<tr> <td> authCode </td><td> String </td><td>否</td><td>客户自定义验证码，长度为 4 ～ 10 位，支持字母和数字。</br>
如果设置了该参数，则 codeLen 参数无效</td></tr>
<tr> <td> needUp </td><td> Boolean </td><td>否</td><td>是否需要支持短信上行。true:需要，false:不需要</br>
说明：如果开通了短信上行抄送功能，该参数需要设置为 true，其它情况设置无效</td></tr>
</table>
:::
::::::

::: note note
- 语音验证码不需要申请签名，开通短信功能时会生成固定的模板 ID（不可自定义或者编辑）。
- 语音验证码如需自定义验证码内容需使用固定参数：authCode，可参考旧版参数说明。
- 2025 年 11 月 5 日之前接入短信的客户可参考旧版参数说明。
:::

### 请求示例

:::::: div linked-codes
::: code Java
```Java
package com.netease.sms.v2;

import java.util.ArrayList;
import java.util.Date;
import java.util.List;
import java.util.HashMap;
import java.util.Map;

import org.apache.http.HttpResponse;
import org.apache.http.NameValuePair;
import org.apache.http.client.entity.UrlEncodedFormEntity;
import org.apache.http.client.methods.HttpPost;
import org.apache.http.impl.client.DefaultHttpClient;
import org.apache.http.message.BasicNameValuePair;
import org.apache.http.util.EntityUtils;

import com.netease.checksum.CheckSumBuilder;
import com.alibaba.fastjson.JSON;

/**
 * 发送文本验证码短信(V2)
 * 模板示例：你的验证码是#{code}
 * 
 * @author sms-team
 */
public class SendCodeV2 {
    
    private static final String SERVER_URL = "https://sms.yunxinapi.com/sms/sendcode.action";
    private static final String APP_KEY = "your_app_key";
    private static final String APP_SECRET = "your_app_secret";
    private static final String NONCE = "123456";

    public static void main(String[] args) throws Exception {
        
        DefaultHttpClient httpClient = new DefaultHttpClient();
        HttpPost httpPost = new HttpPost(SERVER_URL);
        String curTime = String.valueOf((new Date()).getTime() / 1000L);
        String checkSum = CheckSumBuilder.getCheckSum(APP_SECRET, NONCE, curTime);

        // 设置请求头
        httpPost.addHeader("AppKey", APP_KEY);
        httpPost.addHeader("Nonce", NONCE);
        httpPost.addHeader("CurTime", curTime);
        httpPost.addHeader("CheckSum", checkSum);
        httpPost.addHeader("Content-Type", "application/x-www-form-urlencoded;charset=utf-8");

        List<NameValuePair> nvps = new ArrayList<NameValuePair>();
        
        // 基础参数
        nvps.add(new BasicNameValuePair("mobile", "13888888888"));
        nvps.add(new BasicNameValuePair("templateid", "123456"));
        
        // 模板参数映射 - 对应模板：你的验证码是#{code}
        Map<String, String> paramMap = new HashMap<>();
        paramMap.put("code", "123456");
        nvps.add(new BasicNameValuePair("paramMap", JSON.toJSONString(paramMap)));

        httpPost.setEntity(new UrlEncodedFormEntity(nvps, "utf-8"));

        // 执行请求
        HttpResponse response = httpClient.execute(httpPost);
        System.out.println(EntityUtils.toString(response.getEntity(), "utf-8"));
    }
}
```
:::
::: code C#
```C#
using System;
using System.Collections.Generic;
using System.Text;
using System.Security.Cryptography;
using System.Net;
using System.IO;
using Newtonsoft.Json;

namespace SmsApiV2
{
    /// <summary>
    /// 发送文本验证码短信(V2)
    /// 模板示例：你的验证码是#{code}
    /// </summary>
    public class SendCodeV2
    {
        private static string SERVER_URL = "https://sms.yunxinapi.com/sms/sendcode.action";
        private static string APP_KEY = "your_app_key";
        private static string APP_SECRET = "your_app_secret";

        public static void Main(string[] args)
        {
            try
            {
                // 示例调用 - 对应模板：你的验证码是#{code}
                string mobile = "13888888888";
                string templateId = "123456";
                
                var paramMap = new Dictionary<string, string>
                {
                    {"code", "123456"}
                };
                
                SendCode(mobile, templateId, paramMap);
            }
            catch (Exception ex)
            {
                Console.WriteLine("Error: " + ex.Message);
            }
        }

        public static void SendCode(string mobile, string templateId, Dictionary<string, string> paramMap)
        {
            // 生成认证参数
            string nonce = Guid.NewGuid().ToString().Replace("-", "");
            TimeSpan ts = DateTime.Now.ToUniversalTime() - new DateTime(1970, 1, 1);
            string curTime = Convert.ToInt32(ts.TotalSeconds).ToString();
            string checkSum = GetCheckSum(APP_SECRET, nonce, curTime);

            // 构建请求参数
            var postData = new List<string>
            {
                $"mobile={Uri.EscapeDataString(mobile)}",
                $"templateid={templateId}",
                $"paramMap={Uri.EscapeDataString(JsonConvert.SerializeObject(paramMap))}"
            };

            string postDataString = string.Join("&", postData);

            // 发送请求
            HttpWebRequest request = (HttpWebRequest)WebRequest.Create(SERVER_URL);
            request.Method = "POST";
            request.ContentType = "application/x-www-form-urlencoded;charset=utf-8";
            
            // 设置请求头
            request.Headers.Add("AppKey", APP_KEY);
            request.Headers.Add("Nonce", nonce);
            request.Headers.Add("CurTime", curTime);
            request.Headers.Add("CheckSum", checkSum);

            // 写入请求数据
            byte[] postBytes = Encoding.UTF8.GetBytes(postDataString);
            request.ContentLength = postBytes.Length;
            using (Stream requestStream = request.GetRequestStream())
            {
                requestStream.Write(postBytes, 0, postBytes.Length);
            }

            // 获取响应
            using (HttpWebResponse response = (HttpWebResponse)request.GetResponse())
            using (StreamReader reader = new StreamReader(response.GetResponseStream()))
            {
                string responseText = reader.ReadToEnd();
                Console.WriteLine("Response: " + responseText);
            }
        }

        private static string GetCheckSum(string appSecret, string nonce, string curTime)
        {
            string input = appSecret + nonce + curTime;
            using (SHA1 sha1 = SHA1.Create())
            {
                byte[] hashBytes = sha1.ComputeHash(Encoding.UTF8.GetBytes(input));
                return BitConverter.ToString(hashBytes).Replace("-", "").ToLower();
            }
        }
    }
}
```
:::
::: code Python
```Python
# coding=utf-8
import hashlib
import time
import requests
import json

def send_code_v2(mobile, template_id, param_map):
    """
    发送文本验证码短信(V2)
    模板示例：你的验证码是#{code}
    
    Args:
        mobile: 目标手机号
        template_id: 模板ID
        param_map: 模板参数映射
    """
    url = 'https://sms.yunxinapi.com/sms/sendcode.action'
    
    # 认证信息
    app_key = "your_app_key"
    app_secret = "your_app_secret"
    
    # 生成认证参数
    nonce = hashlib.new('sha512', str(time.time()).encode("utf-8")).hexdigest()
    curtime = str(int(time.time()))
    check_sum = hashlib.sha1((app_secret + nonce + curtime).encode("utf-8")).hexdigest()

    # 请求头
    headers = {
        "AppKey": app_key,
        "Nonce": nonce,
        "CurTime": curtime,
        "CheckSum": check_sum,
        "Content-Type": "application/x-www-form-urlencoded;charset=utf-8"
    }

    # 请求参数
    data = {
        'mobile': mobile,
        'templateid': template_id,
        'paramMap': json.dumps(param_map)
    }

    response = requests.post(url, data=data, headers=headers)
    print("Response:", response.text)
    return response.json()

if __name__ == '__main__':
    # 示例调用 - 对应模板：你的验证码是#{code}
    mobile = "13888888888"
    template_id = 123456
    param_map = {"code": "123456"}
    
    send_code_v2(mobile, template_id, param_map)
```
:::
::: code PHP
```PHP
<?php

/**
 * 发送文本验证码短信(V2)
 * 模板示例：你的验证码是#{code}
 * 
 * @author sms-team
 */
class SendCodeV2
{
    private $appKey;
    private $appSecret;
    
    public function __construct($appKey, $appSecret)
    {
        $this->appKey = $appKey;
        $this->appSecret = $appSecret;
    }
    
    /**
     * 发送验证码短信
     * 
     * @param string $mobile 手机号
     * @param string $templateId 模板ID
     * @param array $paramMap 模板参数映射
     * @return array 响应结果
     */
    public function sendCode($mobile, $templateId, $paramMap)
    {
        $url = 'https://sms.yunxinapi.com/sms/sendcode.action';
        
        // 生成认证参数
        $nonce = $this->generateNonce();
        $curTime = time();
        $checkSum = sha1($this->appSecret . $nonce . $curTime);
        
        // 设置请求头
        $headers = [
            'AppKey: ' . $this->appKey,
            'Nonce: ' . $nonce,
            'CurTime: ' . $curTime,
            'CheckSum: ' . $checkSum,
            'Content-Type: application/x-www-form-urlencoded;charset=utf-8'
        ];
        
        // 构建请求参数
        $data = [
            'mobile' => $mobile,
            'templateid' => $templateId,
            'paramMap' => json_encode($paramMap)
        ];
        
        // 发送请求
        return $this->sendRequest($url, $data, $headers);
    }
    
    private function generateNonce($length = 32)
    {
        return substr(md5(uniqid(rand(), true)), 0, $length);
    }
    
    private function sendRequest($url, $data, $headers)
    {
        $ch = curl_init();
        curl_setopt_array($ch, [
            CURLOPT_URL => $url,
            CURLOPT_POST => true,
            CURLOPT_POSTFIELDS => http_build_query($data),
            CURLOPT_HTTPHEADER => $headers,
            CURLOPT_RETURNTRANSFER => true,
            CURLOPT_SSL_VERIFYPEER => false,
            CURLOPT_TIMEOUT => 30
        ]);
        
        $response = curl_exec($ch);
        if (curl_error($ch)) {
            throw new Exception('CURL Error: ' . curl_error($ch));
        }
        curl_close($ch);
        
        return json_decode($response, true);
    }
}

// 使用示例 - 对应模板：你的验证码是#{code}
try {
    $sms = new SendCodeV2('your_app_key', 'your_app_secret');
    
    $mobile = '13888888888';
    $templateId = '123456';
    $paramMap = ['code' => '123456'];
    
    $result = $sms->sendCode($mobile, $templateId, $paramMap);
    echo "发送结果: " . json_encode($result) . "\n";
    
} catch (Exception $e) {
    echo "Error: " . $e->getMessage() . "\n";
}

?>
```
:::
::: code cURL
```cURL
# 发送文本验证码短信(V2)
# 对应模板：你的验证码是#{code}
curl -X POST \
  'https://sms.yunxinapi.com/sms/sendcode.action' \
  -H 'AppKey: your_app_key' \
  -H 'CurTime: 1443592222' \
  -H 'CheckSum: 9e9db3b6c9abb2e1962cf3e6f7316fcc55583f86' \
  -H 'Nonce: 123456' \
  -H 'Content-Type: application/x-www-form-urlencoded;charset=utf-8' \
  -d 'mobile=13888888888' \
  -d 'templateid=123456' \
  -d 'paramMap={"code":"123456"}'
```
:::
::::::

### 返回说明

发送成功则返回相关信息。msg 字段表示此次发送的 sendid。obj 字段表示此次发送的验证码。

```JSON
"Content-Type": "application/json; charset=utf-8"
{
  "code": 200,
  "msg": "88",
  "obj": "1908"
}
```

### 错误码

200、315、403、414、416、500

具体请参考 [通用状态码](#通用状态码)

## 校验验证码

校验指定手机号码的验证码是否合法。

### 请求 URL

```
POST https://sms.yunxinapi.com/sms/verifycode.action HTTP/1.1
Content-Type:application/x-www-form-urlencoded;charset=utf-8
```

### 请求头

请求头的参数说明请参考 [请求头](https://doc.yunxin.163.com/messaging/server-apis/jk3MzY2MTI?platform=server#请求头参数)。

### 参数说明

<table><thead><tr> <th>参数</th><th>类型</th><th>是否必需</th><th>说明</th></tr></thead>
<tr> <td>mobile</td><td>String</td><td>是</td><td>目标手机号码，非中国大陆手机号码需要填写国家代码(如美国：+1-xxxxxxxxxx)或地区代码(如香港：+852-xxxxxxxx)</td></tr>
<tr> <td>code</td><td>String</td><td>是</td><td>验证码</td></tr>
</table>

### 请求示例

```cURL
curl -X POST -H "AppKey: go9dnk49bkd9jd9vmel1kglw0803mgq3" -H "CurTime: 1443592222" -H "CheckSum: 9e9db3b6c9abb2e1962cf3e6f7316fcc55583f86" -H "Nonce: 4tgggergigwow323t23t" -H "Content-Type: application/x-www-form-urlencoded" -d 'mobile=13812345678&code=1234' 'https://sms.yunxinapi.com/sms/verifycode.action'
```

### 返回说明

```JSON
"Content-Type": "application/json; charset=utf-8"
{
  "code":200
}
```

### 错误码

200、301、315、403、404、413、414、500

具体请参考 [通用状态码](#通用状态码)

## 发送通知类和运营类短信

向手机号码发送内容格式预定义的短信，整个短信的内容由模板和变量组成。

### 请求 URL

```
POST https://sms.yunxinapi.com/sms/sendtemplate.action HTTP/1.1
Content-Type:application/x-www-form-urlencoded;charset=utf-8
```

### 请求头

请求头的参数说明请参考 [请求头](https://doc.yunxin.163.com/messaging/server-apis/jk3MzY2MTI?platform=server#请求头参数)。

### 参数说明

:::::: div linked-codes
::: code 新版（2025/11/5）
<table><thead><tr> <th>参数</th><th>类型</th><th>是否必需</th><th>说明</th></tr></thead>
<tr> <td>templateid</td><td>Long</td><td>是</td><td>模板 ID，模板通过后可在模板列表页面获取。</td></tr>
<tr> <td>mobiles</td><td>String</td><td>是</td><td>接收者号码列表，JSONArray 格式,如["186xxxxxxxx","186xxxxxxxx"]，限制接收者号码个数最多为 100 个。<br/>
非中国大陆手机号码需要填写国家代码(如美国：+1-xxxxxxxxxx)或地区代码(如香港：+852-xxxxxxxx)</td></tr>
<tr> <td>paramMap</td><td>String</td><td>否</td><td>短信参数列表，用于依次填充模板，JSONObject格式，例如：{"name":"张三","性别":"男"}</td></tr>
</table>
:::
::: code 旧版
<table><thead><tr> <th>参数</th><th>类型</th><th>是否必需</th><th>说明</th></tr></thead>
<tr> <td>templateid</td><td>int</td><td>是</td><td>模板编号(由您的网易云信客户经理配置之后告知您)</td></tr>
<tr> <td>mobiles</td><td>String</td><td>是</td><td>接收者号码列表，JSONArray 格式,如["186xxxxxxxx","186xxxxxxxx"]，限制接收者号码个数最多为 100 个。<br/>
非中国大陆手机号码需要填写国家代码(如美国：+1-xxxxxxxxxx)或地区代码(如香港：+852-xxxxxxxx)</td></tr>
<tr> <td>params</td><td>String</td><td>模板中 <b>若含变量则必须</b> 包含此参数</td><td>短信参数列表，用于依次填充模板，JSONArray 格式，每个变量长度不能超过 30 字，如 `["xxx","yyy"]`;对于不包含变量的模板，不填此参数表示模板即短信全文内容</td></tr>
<tr> <td> needUp </td><td> Boolean </td><td>否</td><td>是否需要支持短信上行。true:需要，false:不需要</br>
说明：如果开通了短信上行抄送功能，该参数需要设置为 true，其它情况设置无效</td></tr>
</table>
:::
::::::

### 请求示例

:::::: div linked-codes
::: code Java
```Java
package com.netease.sms.v2;

import java.util.ArrayList;
import java.util.Date;
import java.util.List;
import java.util.HashMap;
import java.util.Map;
import java.util.Arrays;

import org.apache.http.HttpResponse;
import org.apache.http.NameValuePair;
import org.apache.http.client.entity.UrlEncodedFormEntity;
import org.apache.http.client.methods.HttpPost;
import org.apache.http.impl.client.DefaultHttpClient;
import org.apache.http.message.BasicNameValuePair;
import org.apache.http.util.EntityUtils;

import com.netease.checksum.CheckSumBuilder;
import com.alibaba.fastjson.JSON;

/**
 * 发送通知/营销模板短信(V2)
 * 模板示例：你的取件码是#{code}，请到#{address}领取，截止时间#{time}
 * 
 * @author sms-team
 */
public class SendTemplateV2 {
    
    private static final String SERVER_URL = "https://sms.yunxinapi.com/sms/sendtemplate.action";
    private static final String APP_KEY = "your_app_key";
    private static final String APP_SECRET = "your_app_secret";
    private static final String NONCE = "123456";

    public static void main(String[] args) throws Exception {
        
        DefaultHttpClient httpClient = new DefaultHttpClient();
        HttpPost httpPost = new HttpPost(SERVER_URL);
        String curTime = String.valueOf((new Date()).getTime() / 1000L);
        String checkSum = CheckSumBuilder.getCheckSum(APP_SECRET, NONCE, curTime);

        // 设置请求头
        httpPost.addHeader("AppKey", APP_KEY);
        httpPost.addHeader("Nonce", NONCE);
        httpPost.addHeader("CurTime", curTime);
        httpPost.addHeader("CheckSum", checkSum);
        httpPost.addHeader("Content-Type", "application/x-www-form-urlencoded;charset=utf-8");

        List<NameValuePair> nvps = new ArrayList<NameValuePair>();
        
        // 基础参数
        nvps.add(new BasicNameValuePair("templateid", "789123"));
        
        // 手机号列表
        List<String> mobiles = Arrays.asList("13888888888", "13666666666");
        nvps.add(new BasicNameValuePair("mobiles", JSON.toJSONString(mobiles)));
        
        // 模板参数映射 - 对应模板：你的取件码是#{code}，请到#{address}领取，截止时间#{time}
        Map<String, String> paramMap = new HashMap<>();
        paramMap.put("code", "TK789456");
        paramMap.put("address", "北京市朝阳区SOHO现代城A座1层快递柜");
        paramMap.put("time", "2024年12月15日18:00");
        nvps.add(new BasicNameValuePair("paramMap", JSON.toJSONString(paramMap)));

        httpPost.setEntity(new UrlEncodedFormEntity(nvps, "utf-8"));

        // 执行请求
        HttpResponse response = httpClient.execute(httpPost);
        System.out.println(EntityUtils.toString(response.getEntity(), "utf-8"));
    }
}
```
:::
::: code C#
```C#
using System;
using System.Collections.Generic;
using System.Text;
using System.Security.Cryptography;
using System.Net;
using System.IO;
using Newtonsoft.Json;

namespace SmsApiV2
{
    /// <summary>
    /// 发送文本验证码短信(V2)
    /// 模板示例：你的验证码是#{code}
    /// </summary>
    public class SendCodeV2
    {
        private static string SERVER_URL = "https://sms.yunxinapi.com/sms/sendcode.action";
        private static string APP_KEY = "your_app_key";
        private static string APP_SECRET = "your_app_secret";

        public static void Main(string[] args)
        {
            try
            {
                // 示例调用 - 对应模板：你的验证码是#{code}
                string mobile = "13888888888";
                string templateId = "123456";
                
                var paramMap = new Dictionary<string, string>
                {
                    {"code", "123456"}
                };
                
                SendCode(mobile, templateId, paramMap);
            }
            catch (Exception ex)
            {
                Console.WriteLine("Error: " + ex.Message);
            }
        }

        public static void SendCode(string mobile, string templateId, Dictionary<string, string> paramMap)
        {
            // 生成认证参数
            string nonce = Guid.NewGuid().ToString().Replace("-", "");
            TimeSpan ts = DateTime.Now.ToUniversalTime() - new DateTime(1970, 1, 1);
            string curTime = Convert.ToInt32(ts.TotalSeconds).ToString();
            string checkSum = GetCheckSum(APP_SECRET, nonce, curTime);

            // 构建请求参数
            var postData = new List<string>
            {
                $"mobile={Uri.EscapeDataString(mobile)}",
                $"templateid={templateId}",
                $"paramMap={Uri.EscapeDataString(JsonConvert.SerializeObject(paramMap))}"
            };

            string postDataString = string.Join("&", postData);

            // 发送请求
            HttpWebRequest request = (HttpWebRequest)WebRequest.Create(SERVER_URL);
            request.Method = "POST";
            request.ContentType = "application/x-www-form-urlencoded;charset=utf-8";
            
            // 设置请求头
            request.Headers.Add("AppKey", APP_KEY);
            request.Headers.Add("Nonce", nonce);
            request.Headers.Add("CurTime", curTime);
            request.Headers.Add("CheckSum", checkSum);

            // 写入请求数据
            byte[] postBytes = Encoding.UTF8.GetBytes(postDataString);
            request.ContentLength = postBytes.Length;
            using (Stream requestStream = request.GetRequestStream())
            {
                requestStream.Write(postBytes, 0, postBytes.Length);
            }

            // 获取响应
            using (HttpWebResponse response = (HttpWebResponse)request.GetResponse())
            using (StreamReader reader = new StreamReader(response.GetResponseStream()))
            {
                string responseText = reader.ReadToEnd();
                Console.WriteLine("Response: " + responseText);
            }
        }

        private static string GetCheckSum(string appSecret, string nonce, string curTime)
        {
            string input = appSecret + nonce + curTime;
            using (SHA1 sha1 = SHA1.Create())
            {
                byte[] hashBytes = sha1.ComputeHash(Encoding.UTF8.GetBytes(input));
                return BitConverter.ToString(hashBytes).Replace("-", "").ToLower();
            }
        }
    }
}
```
:::
::: code Python
```Python
# coding=utf-8
import hashlib
import time
import requests
import json

def send_template_v2(mobiles, template_id, param_map):
    """
    发送通知/营销模板短信(V2)
    模板示例：你的取件码是#{code}，请到#{address}领取，截止时间#{time}
    
    Args:
        mobiles: 手机号列表
        template_id: 模板ID
        param_map: 模板参数映射
    """
    url = 'https://sms.yunxinapi.com/sms/sendtemplate.action'
    
    # 认证信息
    app_key = "your_app_key"
    app_secret = "your_app_secret"
    
    # 生成认证参数
    nonce = hashlib.new('sha512', str(time.time()).encode("utf-8")).hexdigest()
    curtime = str(int(time.time()))
    check_sum = hashlib.sha1((app_secret + nonce + curtime).encode("utf-8")).hexdigest()

    # 请求头
    headers = {
        "AppKey": app_key,
        "Nonce": nonce,
        "CurTime": curtime,
        "CheckSum": check_sum,
        "Content-Type": "application/x-www-form-urlencoded;charset=utf-8"
    }

    # 请求参数
    data = {
        'mobiles': json.dumps(mobiles),
        'templateid': template_id,
        'paramMap': json.dumps(param_map)
    }

    response = requests.post(url, data=data, headers=headers)
    print("Response:", response.text)
    return response.json()

if __name__ == '__main__':
    # 示例调用 - 对应模板：你的取件码是#{code}，请到#{address}领取，截止时间#{time}
    mobiles = ["13888888888", "13666666666"]
    template_id = 789123
    
    param_map = {
        "code": "TK789456",
        "address": "北京市朝阳区SOHO现代城A座1层快递柜",
        "time": "2024年12月15日18:00"
    }
    
    send_template_v2(mobiles, template_id, param_map)
```
:::
::: code PHP
```PHP
<?php

/**
 * 发送文本验证码短信(V2)
 * 模板示例：你的验证码是#{code}
 * 
 * @author sms-team
 */
class SendCodeV2
{
    private $appKey;
    private $appSecret;
    
    public function __construct($appKey, $appSecret)
    {
        $this->appKey = $appKey;
        $this->appSecret = $appSecret;
    }
    
    /**
     * 发送验证码短信
     * 
     * @param string $mobile 手机号
     * @param string $templateId 模板ID
     * @param array $paramMap 模板参数映射
     * @return array 响应结果
     */
    public function sendCode($mobile, $templateId, $paramMap)
    {
        $url = 'https://sms.yunxinapi.com/sms/sendcode.action';
        
        // 生成认证参数
        $nonce = $this->generateNonce();
        $curTime = time();
        $checkSum = sha1($this->appSecret . $nonce . $curTime);
        
        // 设置请求头
        $headers = [
            'AppKey: ' . $this->appKey,
            'Nonce: ' . $nonce,
            'CurTime: ' . $curTime,
            'CheckSum: ' . $checkSum,
            'Content-Type: application/x-www-form-urlencoded;charset=utf-8'
        ];
        
        // 构建请求参数
        $data = [
            'mobile' => $mobile,
            'templateid' => $templateId,
            'paramMap' => json_encode($paramMap)
        ];
        
        // 发送请求
        return $this->sendRequest($url, $data, $headers);
    }
    
    private function generateNonce($length = 32)
    {
        return substr(md5(uniqid(rand(), true)), 0, $length);
    }
    
    private function sendRequest($url, $data, $headers)
    {
        $ch = curl_init();
        curl_setopt_array($ch, [
            CURLOPT_URL => $url,
            CURLOPT_POST => true,
            CURLOPT_POSTFIELDS => http_build_query($data),
            CURLOPT_HTTPHEADER => $headers,
            CURLOPT_RETURNTRANSFER => true,
            CURLOPT_SSL_VERIFYPEER => false,
            CURLOPT_TIMEOUT => 30
        ]);
        
        $response = curl_exec($ch);
        if (curl_error($ch)) {
            throw new Exception('CURL Error: ' . curl_error($ch));
        }
        curl_close($ch);
        
        return json_decode($response, true);
    }
}

// 使用示例 - 对应模板：你的验证码是#{code}
try {
    $sms = new SendCodeV2('your_app_key', 'your_app_secret');
    
    $mobile = '13888888888';
    $templateId = '123456';
    $paramMap = ['code' => '123456'];
    
    $result = $sms->sendCode($mobile, $templateId, $paramMap);
    echo "发送结果: " . json_encode($result) . "\n";
    
} catch (Exception $e) {
    echo "Error: " . $e->getMessage() . "\n";
}

?>
```
:::
::: code cURL
```curl
# 发送文本验证码短信(V2)
# 对应模板：你的验证码是#{code}
curl -X POST \
  'https://sms.yunxinapi.com/sms/sendcode.action' \
  -H 'AppKey: your_app_key' \
  -H 'CurTime: 1443592222' \
  -H 'CheckSum: 9e9db3b6c9abb2e1962cf3e6f7316fcc55583f86' \
  -H 'Nonce: 123456' \
  -H 'Content-Type: application/x-www-form-urlencoded;charset=utf-8' \
  -d 'mobile=13888888888' \
  -d 'templateid=123456' \
  -d 'paramMap={"code":"123456"}'
```
:::
::::::

### 返回说明

成功则在 obj 中返回此次发送的 sendid(long)，用于查询发送结果。

```JSON
"Content-Type": "application/json; charset=utf-8"
{
  "code":200,
  "msg":"sendid",
  "obj":123
}
```

### 错误码

200、315、403、413、414、500

具体请参考 [通用状态码](#通用状态码)

## 查询通知类和运营类短信发送状态

根据短信的 sendid (`sendtemplate.action` 接口中的返回值)，查询短信发送结果。

### 请求 URL

```
POST https://sms.yunxinapi.com/sms/querystatus.action HTTP/1.1
Content-Type:application/x-www-form-urlencoded;charset=utf-8
```

### 请求头

请求头的参数说明请参考 [请求头](https://doc.yunxin.163.com/messaging/server-apis/jk3MzY2MTI?platform=server#请求头参数)。

### 参数说明

<table><thead><tr> <th>参数</th><th>类型</th><th>是否必需</th><th>说明</th></tr></thead>
<tr> <td>sendid</td><td>long</td><td>是</td><td>发送短信的编号 sendid
</td></tr>
</table>

### 请求示例

```cURL
curl -X POST -H "AppKey: go9dnk49bkd9jd9vmel1kglw0803mgq3" -H "CurTime: 1443592222" -H "CheckSum: 9e9db3b6c9abb2e1962cf3e6f7316fcc55583f86" -H "Nonce: 4tgggergigwow323t23t" -H "charset: utf-8" -H "Content-Type: application/x-www-form-urlencoded" -d 'sendid=1' 'https://sms.yunxinapi.com/sms/querystatus.action'
```

### 返回说明

obj 中返回 JSONArray，格式如下(其中 status 取值：0-未发送，1-发送成功（提交通道成功），2-发送失败（提交通道失败），3-反垃圾)。

```JSON
"Content-Type": "application/json; charset=utf-8"
{
  "code": 200,
  "obj": [
    {
      "status": 1,
      "mobile": "13812341234",
      "updatetime": 1471234567812
    }
  ]
}
```

### 错误码

200、315、403、404、413、414、500

具体请参考 [通用状态码](#通用状态码)

## 发送视频短信

向手机号码发送内容格式预定义的视频短信，整个短信的内容由文本和多媒体组成。

### 请求 URL

```
POST https://sms.yunxinapi.com/sms-new-api/video/template/send HTTP/1.1
Content-Type:application/x-www-form-urlencoded;charset=utf-8
```

### 请求头

请求头的参数说明请参考 [请求头](https://doc.yunxin.163.com/messaging/server-apis/jk3MzY2MTI?platform=server#请求头参数)。

### 参数说明

<table><thead><tr> <th>参数</th><th>类型</th><th>是否必需</th><th>说明</th></tr></thead>
<tr> <td>templateId</td><td>long</td><td>是</td><td>模板编号(审核通过的视频短信多媒体模板 ID)</td></tr>
<tr> <td>mobiles</td><td>String</td><td>是</td><td>接收者号码列表，JSONArray 格式,如["186xxxxxxxx","186xxxxxxxx"]，限制接收者号码个数最多为 100 个。<br/>
目前只支持国内号码</td></tr>
<tr> <td>params</td><td>String</td><td>否若模板中包含变量则该参数必填</td><td>模板参数，JSONObject 格式，如 {"name": "网易云信","age":6}，其中 name、age 为视频模板中的参数#{name},#{age}</td></tr>
</table>

### 请求示例

```cURL
curl -X POST -H "AppKey: go9dnk49bkd9jd9vmel1kglw0803mgq3" -H "CurTime: 1443592222" -H "CheckSum: 9e9db3b6c9abb2e1962cf3e6f7316fcc55583f86" -H "Nonce: 4tgggergigwow323t23t" -H "charset: utf-8" -H "Content-Type: application/x-www-form-urlencoded" -d 'templateId=1007&mobiles=["13812345678"]&params={"name": "网易云信","age":6}' 'https://sms.yunxinapi.com/sms-new-api/video/template/send'
```

### 返回说明

成功则在 obj 中返回此次发送的 sendid(long)，用于查询发送结果。

```JSON
"Content-Type": "application/json; charset=utf-8"
{
  "code":200,
  "msg":"sendid",
  "obj":123
}
```

### 错误码

200、315、403、413、414、500

具体请参考 [通用状态码](#通用状态码)

## 通用状态码

所有的短信的 HTTP 响应体均由两部分组成：

```JSON
{
    "code": xxx; // HTTP 状态码，返回值分为 200（代表成功）和其他（代表失败）。
    "msg": xxx; // `code` 返回的不是 200 时，会返回 `msg` 描述失败原因。
}
```

<style>
table th:first-of-type {
    width: 20%;
}
</style>

您可以在以下列表中查询状态码，排查和解决 HTTP 请求错误。

| <div style="width: 50px;">code</div> | 原因 | 解决方法 |
| ---- | ---- | ---- |
| 400 | 语法格式有误，服务器无法理解此请求 | 排查请求包体与请求 URL 是否匹配。 |
| 403 | 无权限 | 您的应用没有开通短信服务，请至 [网易云信控制台](https://app.yunxin.163.com/global/home) **应用管理 > 产品功能 > 短信** 查看是否已开启短信服务（欠费关停后需重新开启短信服务）。 |
| 404 | 目标(对象或用户)不存在 | 检查短信模板或对应变量是否存在，具体请参考返回的 `msg`。 |
| 412 | 黑名单号码 | 用户对营销短信回复过退订（TD），如用户自愿解除请 [提交工单](https://app.yunxin.163.com/global/service/ticket/create) 联系网易云信技术支持工程师。 |
| 413 | 验证码校验失败 | 调用校验验证码接口时超过了设置的验证码有效期，请至网易云信控制台 **应用管理 > 产品功能 > 短信 > 安全设置 > 验证码** 查看验证码有效期（默认 5 分钟）。 |
| 414 | 客户端提交了非法参数 | 请检查对应参数是否合法，具体请参考返回的 `msg`。 |
| 416 | 操作过于频繁 | 发送频率超过设置的频控，或设置了短信禁发国家。请至 [网易云信控制台](https://app.yunxin.163.com/global/home) **应用管理 > 产品功能 > 短信 > 安全设置** 查看频控和禁发国家（上限 25 条/天）。 |
| 426 | 境外 IP 拦截 | 目标号码为国内手机号，请使用国内 IP 发送。特殊情况请联系商务说明详情。
| 601 | 内容反垃圾 | 短信内容命中敏感词汇，详情可以 [提交工单](https://app.yunxin.163.com/global/service/ticket/create) 联系网易云信技术支持工程师。 |

## 历史请求示例参考

### 发送短信验证码

:::::: div linked-codes
::: code Java
```Java
package com.netease.sms;
import java.util.ArrayList;
import java.util.Date;
import java.util.List;

import org.apache.http.HttpResponse;
import org.apache.http.NameValuePair;
import org.apache.http.client.entity.UrlEncodedFormEntity;
import org.apache.http.client.methods.HttpPost;
import org.apache.http.impl.client.DefaultHttpClient;
import org.apache.http.message.BasicNameValuePair;
import org.apache.http.util.EntityUtils;

import com.netease.checksum.CheckSumBuilder;
/**
 * 发送验证码
 * @author liuxuanlin
 *
 */
public class SendCode {
    //发送验证码的请求路径 URL
    private static final String
            SERVER_URL="https://sms.yunxinapi.com/sms/sendcode.action";
    //网易云信分配的账号，请替换您在网易云信控制台应用下创建的 Appkey
    private static final String
            APP_KEY="fd460d34e786e7754e505bc4fab0f027";
    //网易云信分配的密钥，请替换您在网易云信控制台应用下创建的 appSecret
    private static final String APP_SECRET="xxxxxxxx";
    //随机数
    private static final String NONCE="123456";
    //短信模板 ID
    private static final String TEMPLATEID="3057527";
    //手机号
    private static final String MOBILE="13888888888";
    //验证码长度，范围 4～10，默认为 4
    private static final Int CODELEN=6;

    public static void main(String[] args) throws Exception {

        DefaultHttpClient httpClient = new DefaultHttpClient();
        HttpPost httpPost = new HttpPost(SERVER_URL);
        String curTime = String.valueOf((new Date()).getTime() / 1000L);
        /*
         * 参考计算 CheckSum 的 java 代码，在上述文档的参数列表中，有 CheckSum 的计算文档示例
         */
        String checkSum = CheckSumBuilder.getCheckSum(APP_SECRET, NONCE, curTime);

        // 设置请求的 header
        httpPost.addHeader("AppKey", APP_KEY);
        httpPost.addHeader("Nonce", NONCE);
        httpPost.addHeader("CurTime", curTime);
        httpPost.addHeader("CheckSum", checkSum);
        httpPost.addHeader("Content-Type", "application/x-www-form-urlencoded;charset=utf-8");

        // 设置请求的的参数，requestBody 参数
        List<NameValuePair> nvps = new ArrayList<NameValuePair>();
        /*
         * 1.如果是模板短信，请注意参数 mobile 是有 s 的，详细参数配置请参考 **发送模板短信文档**
         * 2.参数格式是 jsonArray 的格式，例如 "['13888888888','13666666666']"
         * 3.params 是根据您模板里面有几个参数，那里面的参数也是 jsonArray 格式
         */
        nvps.add(new BasicNameValuePair("templateid", TEMPLATEID));
        nvps.add(new BasicNameValuePair("mobile", MOBILE));
        nvps.add(new BasicNameValuePair("codeLen", CODELEN));

        httpPost.setEntity(new UrlEncodedFormEntity(nvps, "utf-8"));

        // 执行请求
        HttpResponse response = httpClient.execute(httpPost);
        /*
         * 1.打印执行结果，打印结果一般会 200、315、403、404、413、414、500
         * 2.具体的 code 有问题的可以参考官网的 Code 状态表
         */
        System.out.println(EntityUtils.toString(response.getEntity(), "utf-8"));
    }
}
```
:::
::: code C#

```C#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Security.Cryptography;
using System.Net;
using System.IO;

namespace server_http_api
{
    class CheckSumBuilder
    {
        // 计算并获取 CheckSum
        public static String getCheckSum(String appSecret, String nonce, String curTime)
        {
            byte[] data = Encoding.Default.GetBytes(appSecret + nonce + curTime);
            byte[] result;

            SHA1 sha = new SHA1CryptoServiceProvider();
            // This is one implementation of the abstract class SHA1.
            result = sha.ComputeHash(data);

            return getFormattedText(result);
        }

        // 计算并获取 md5 值
        public static String getMD5(String requestBody)
        {
            if (requestBody == null)
                return null;

            // Create a new instance of the MD5CryptoServiceProvider object.
            MD5 md5Hasher = MD5.Create();

            // Convert the input string to a byte array and compute the hash.
            byte[] data = md5Hasher.ComputeHash(Encoding.Default.GetBytes(requestBody));

            // Create a new Stringbuilder to collect the bytes
            // and create a string.
            StringBuilder sBuilder = new StringBuilder();

            // Loop through each byte of the hashed data
            // and format each one as a hexadecimal string.
            for (int i = 0; i < data.Length; i++)
            {
                sBuilder.Append(data[i].ToString("x2"));
            }

            // Return the hexadecimal string.
            return getFormattedText(Encoding.Default.GetBytes(sBuilder.ToString()));
        }

        private static String getFormattedText(byte[] bytes)
        {
            char[] HEX_DIGITS = { '0', '1', '2', '3', '4', '5',
            '6', '7', '8', '9', 'a', 'b', 'c', 'd', 'e', 'f' };
            int len = bytes.Length;
            StringBuilder buf = new StringBuilder(len * 2);
            for (int j = 0; j < len; j++) {
                buf.Append(HEX_DIGITS[(bytes[j] >> 4) & 0x0f]);
                buf.Append(HEX_DIGITS[bytes[j] & 0x0f]);
            }
            return buf.ToString();
        }
    }

    class HttpClient
    {
        //发起 HTTP 请求
        public static void HttpPost(string url, Stream data, IDictionary<object, string> headers = null)
        {
            System.Net.WebRequest request = HttpWebRequest.Create(url);
            request.Method = "POST";
            if (data != null)
            request.ContentLength = data.Length;
            //request.ContentType = "application/x-www-form-urlencoded;charset=utf-8";

            if (headers != null)
            {
                foreach (var v in headers)
                {
                    if (v.Key is HttpRequestHeader)
                        request.Headers[(HttpRequestHeader)v.Key] = v.Value;
                    else
                        request.Headers[v.Key.ToString()] = v.Value;
                }
            }
            HttpWebResponse response = null;
            try
            {
                // Get the response.
                response = (HttpWebResponse)request.GetResponse();
                // Display the status.
                Console.WriteLine(response.StatusDescription);
                // Get the stream containing content returned by the server.
                Stream dataStream = response.GetResponseStream();
                // Open the stream using a StreamReader for easy access.
                StreamReader reader = new StreamReader(dataStream);
                // Read the content.
                string responseFromServer = reader.ReadToEnd();
                // Display the content.
                Console.WriteLine(responseFromServer);
                // Cleanup the streams and the response.
                reader.Close();
                dataStream.Close();
                response.Close();
            }
            catch (Exception e)
            {
                Console.WriteLine(e.Message);
                Console.WriteLine(response.StatusDescription);
            }
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            String url = "https://sms.yunxinapi.com/sms/sendcode.action";
            url += "?templateid=3030410&mobile=13888888888";//请输入正确的手机号

            //网易云信分配的账号，请替换您在网易云信控制台应用下创建的 Appkey
            String appKey = "fd460d34e786e7754e505bc4fab0f027";
            //网易云信分配的密钥，请替换您在网易云信控制台应用下创建的 appSecret
            String appSecret = "xxxxxxxx";
            //随机数（最大长度 128 个字符）
            String nonce = "12345";

            TimeSpan ts = DateTime.Now.ToUniversalTime() - new DateTime(1970, 1, 1);
            Int32 ticks = System.Convert.ToInt32(ts.TotalSeconds);
            //当前 UTC 时间戳，从 1970 年 1 月 1 日 0 点 0 分 0 秒开始到现在的秒数(String)
            String curTime = ticks.ToString();
            //SHA1(AppSecret + Nonce + CurTime),三个参数拼接的字符串，进行 SHA1 哈希计算，转化成 16 进制字符(String，小写)
            String checkSum = CheckSumBuilder.getCheckSum(appSecret, nonce, curTime);

            IDictionary<object, String> headers = new Dictionary<object, String>();
            headers["AppKey"] = appKey;
            headers["Nonce"] = nonce;
            headers["CurTime"] = curTime;
            headers["CheckSum"] = checkSum;
            headers["ContentType"] = "application/x-www-form-urlencoded;charset=utf-8";
            //执行 HTTP 请求
            HttpClient.HttpPost(url, null, headers);
        }
    }
}
```
:::
::: code Python
```Python
# coding=utf-8
import hashlib
import time
import requests

def send_code(mobile):
    url = 'https://sms.yunxinapi.com/sms/sendcode.action'
    """
    AppKey    网易云信分配的账号，请替换您在网易云信控制台应用下创建的 Appkey
    Nonce    随机数（最大长度 128 个字符）
    CurTime    当前 UTC 时间戳，从 1970 年 1 月 1 日 0 点 0 分 0 秒开始到现在的秒数(String)
    CheckSum    SHA1(AppSecret + Nonce + CurTime)，三个参数拼接的字符串，进行 SHA1 哈希计算，转化成 16 进制字符(String，小写)
    """
    AppKey = ""
    # 生成 128 个长度以内的随机字符串
    nonce = hashlib.new('sha512', str(time.time()).encode("utf-8")).hexdigest()
    # 获取当前时间戳
    curtime = str(int(time.time()))
    # 网易云信的 App Secret
    AppSecret = ""
    # 根据要求进行 SHA1 哈希计算
    check_sum = hashlib.sha1((AppSecret + nonce + curtime).encode("utf-8")).hexdigest()

    header = {
        "AppKey": AppKey,
        "Nonce": nonce,
        "CurTime": curtime,
        "CheckSum": check_sum
    }

    data = {
        'mobile': mobile, # 手机号
        "templateid": 123456,

    }

    resp = requests.post(url, data=data, headers=header)

    print("Response:", resp.content)

if __name__ == '__main__':
    send_code("12345678910") #要发送的手机号
```
:::
::: code PHP
```PHP
<?php

/**
 * 网易云信 server API 简单实例
 * Class ServerAPI
 * @author chensheng dengyuan
 * @created date    2018-02-02 13:45
 *
 *
 ***/

class ServerAPI
{
    public $AppKey;                //网易云信控制台分配的 AppKey
    public $AppSecret;             //网易云信控制台分配的 AppSecret,可刷新
    public $Nonce;                    //随机数（最大长度 128 个字符）
    public $CurTime;                 //当前 UTC 时间戳，从 1970 年 1 月 1 日 0 点 0 分 0 秒开始到现在的秒数(String)
    public $CheckSum;                //SHA1(AppSecret + Nonce + CurTime),三个参数拼接的字符串，进行 SHA1 哈希计算，转化成 16 进制字符(String，小写)
    const HEX_DIGITS = "0123456789abcdef";

    /**
     * 参数初始化
     * @param $AppKey
     * @param $AppSecret
     * @param $RequestType [选择 php 请求方式，fsockopen 或 curl，若为 curl 方式，请检查 php 配置是否开启]
     */
    public function __construct($AppKey, $AppSecret, $RequestType = 'curl')
    {
        $this->AppKey = $AppKey;
        $this->AppSecret = $AppSecret;
        $this->RequestType = $RequestType;
    }

    /**
     * API checksum 校验生成
     * @param void
     * @return $CheckSum(对象私有属性)
     */
    public function checkSumBuilder()
    {
        //此部分生成随机字符串
        $hex_digits = self::HEX_DIGITS;
        $this->Nonce;
        for ($i = 0; $i < 128; $i++) {            //随机字符串最大 128 个字符，也可以小于该数
            $this->Nonce .= $hex_digits[rand(0, 15)];
        }
        $this->CurTime = (string)(time());    //当前时间戳，以秒为单位

        $join_string = $this->AppSecret . $this->Nonce . $this->CurTime;
        $this->CheckSum = sha1($join_string);
        //print_r($this->CheckSum);
    }

    /**
     * 将 json 字符串转化成 php 数组
     * @param $json_str
     * @return $json_arr
     */
    public function json_to_array($json_str)
    {

        if (is_array($json_str) || is_object($json_str)) {
            $json_str = $json_str;
        } else if (is_null(json_decode($json_str))) {
            $json_str = $json_str;
        } else {
            $json_str = strval($json_str);
            $json_str = json_decode($json_str, true);
        }
        $json_arr = array();
        foreach ($json_str as $k => $w) {
            if (is_object($w)) {
                $json_arr[$k] = $this->json_to_array($w); //判断类型是不是 object
            } else if (is_array($w)) {
                $json_arr[$k] = $this->json_to_array($w);
            } else {
                $json_arr[$k] = $w;
            }
        }
        return $json_arr;
    }

    /**
     * 使用 CURL 方式发送 post 请求
     * @param $url     [请求地址]
     * @param $data    [array 格式数据]
     * @return $请求返回结果(array)
     */
    public function postDataCurl($url, $data)
    {
        $this->checkSumBuilder();       //发送请求前需先生成 checkSum

        $timeout = 5000;
        $http_header = array(
            'AppKey:' . $this->AppKey,
            'Nonce:' . $this->Nonce,
            'CurTime:' . $this->CurTime,
            'CheckSum:' . $this->CheckSum,
            'Content-Type:application/x-www-form-urlencoded;charset=utf-8'
        );
        //print_r($http_header);

        // $postdata = '';
        $postdataArray = array();
        foreach ($data as $key => $value) {
            array_push($postdataArray, $key . '=' . urlencode($value));
        }
        $postdata = join('&', $postdataArray);

        // var_dump($postdata);

        $ch = curl_init();
        curl_setopt($ch, CURLOPT_URL, $url);
        curl_setopt($ch, CURLOPT_POST, 1);
        curl_setopt($ch, CURLOPT_POSTFIELDS, $postdata);
        curl_setopt($ch, CURLOPT_HEADER, false);
        curl_setopt($ch, CURLOPT_HTTPHEADER, $http_header);
        curl_setopt($ch, CURLOPT_SSL_VERIFYPEER, false); //处理 http 证书问题
        curl_setopt($ch, CURLOPT_CONNECTTIMEOUT, $timeout);
        curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);

        $result = curl_exec($ch);
        if (false === $result) {
            $result = curl_errno($ch);
        }
        curl_close($ch);
        return $this->json_to_array($result);
    }

    /**
     * 使用 FSOCKOPEN 方式发送 post 请求
     * @param $url     [请求地址]
     * @param $data    [array 格式数据]
     * @return $请求返回结果(array)
     */
    public function postDataFsockopen($url, $data)
    {
        $this->checkSumBuilder();//发送请求前需先生成 checkSum

        $postdata = '';
        foreach ($data as $key => $value) {
            $postdata .= ($key . '=' . urlencode($value) . '&');
        }
        // building POST-request:
        $URL_Info = parse_url($url);
        if (!isset($URL_Info["port"])) {
            $URL_Info["port"] = 80;
        }
        $request = '';
        $request .= "POST " . $URL_Info["path"] . " HTTP/1.1\r\n";
        $request .= "Host:" . $URL_Info["host"] . "\r\n";
        $request .= "Content-type: application/x-www-form-urlencoded;charset=utf-8\r\n";
        $request .= "Content-length: " . strlen($postdata) . "\r\n";
        $request .= "Connection: close\r\n";
        $request .= "AppKey: " . $this->AppKey . "\r\n";
        $request .= "Nonce: " . $this->Nonce . "\r\n";
        $request .= "CurTime: " . $this->CurTime . "\r\n";
        $request .= "CheckSum: " . $this->CheckSum . "\r\n";
        $request .= "\r\n";
        $request .= $postdata . "\r\n";

        print_r($request);
        $fp = fsockopen($URL_Info["host"], $URL_Info["port"]);
        fputs($fp, $request);
        $result = '';
        while (!feof($fp)) {
            $result .= fgets($fp, 128);
        }
        fclose($fp);

        $str_s = strpos($result, '{');
        $str_e = strrpos($result, '}');
        $str = substr($result, $str_s, $str_e - $str_s + 1);
        print_r($result);
        return $this->json_to_array($str);
    }

    /**
     * 发送短信验证码
     * @param $templateid    [模板编号(由客服配置之后告知开发者)]
     * @param $mobile       [目标手机号]
     * @param $deviceId     [目标设备号，可选参数]
     * @return $codeLen      [验证码长度,范围 4～10，默认为 4]
     */
    public function sendSmsCode($templateid, $mobile, $deviceId = '', $codeLen)
    {
        $url = 'https://sms.yunxinapi.com/sms/sendcode.action';
        $data = array(
            'templateid' => $templateid,
            'mobile' => $mobile,
            'deviceId' => $deviceId,
            'codeLen' => $codeLen
        );
        if ($this->RequestType == 'curl') {
            $result = $this->postDataCurl($url, $data);
        } else {
            $result = $this->postDataFsockopen($url, $data);
        }
        return $result;
    }

    /**
     * 发送模板短信
     * @param $templateid       [模板编号(由客服配置之后告知开发者)]
     * @param $mobiles          [验证码]
     * @param $params          [短信参数列表，用于依次填充模板，JSONArray 格式，如["xxx","yyy"];对于不包含变量的模板，不填此参数表示模板即短信全文内容]
     * @return $result      [返回 array 数组对象]
     */
    public function sendSMSTemplate($templateid, $mobiles = array(), $params = '')
    {
        $url = 'https://sms.yunxinapi.com/sms/sendtemplate.action';
        $data = array(
            'templateid' => $templateid,
            'mobiles' => json_encode($mobiles),
            'params' => json_encode($params)
        );
        if ($this->RequestType == 'curl') {
            $result = $this->postDataCurl($url, $data);
        } else {
            $result = $this->postDataFsockopen($url, $data);
        }
        return $result;
    }

}

?>

```
:::
::: code cURL
```cURL
curl -X POST -H "AppKey: go9dnk49bkd9jd9vmel1kglw0803mgq3" -H "CurTime: 1443592222" -H "CheckSum: 9e9db3b6c9abb2e1962cf3e6f7316fcc55583f86" -H "Nonce: 4tgggergigwow323t23t" -H "Content-Type: application/x-www-form-urlencoded" -d 'mobile=13812345678' 'https://sms.yunxinapi.com/sms/sendcode.action'
```
:::
::::::

### 发送通知类和运营类短信

:::::: div linked-codes
::: code Java
```Java
package com.netease.code;

import java.util.ArrayList;
import java.util.Date;
import java.util.List;

import org.apache.http.HttpResponse;
import org.apache.http.NameValuePair;
import org.apache.http.client.entity.UrlEncodedFormEntity;
import org.apache.http.client.methods.HttpPost;
import org.apache.http.impl.client.DefaultHttpClient;
import org.apache.http.message.BasicNameValuePair;
import org.apache.http.util.EntityUtils;

import com.netease.checksum.CheckSumBuilder;
/**
 * 发送模板短信请求
 * @author liuxuanlin
 *
 */
public class SendTemplate {
    //发送通知类和运营类短信的请求路径 URL
    private static final String
            SERVER_URL="https://sms.yunxinapi.com/sms/sendtemplate.action";
    //网易云信分配的账号，请替换您在网易云信控制台应用下创建的 Appkey
    private static final String
            APP_KEY="fd460d34e786e7754e505bc4fab0f027";
    //网易云信分配的密钥，请替换您在网易云信控制台应用下创建的 appSecret
    private static final String APP_SECRET="xxxxxxxx";
    //随机数
    private static final String NONCE="123456";
    //短信模板 ID
    private static final String TEMPLATEID="3057527";
    //手机号，接收者号码列表，JSONArray 格式，限制接收者号码个数最多为 100 个
    private static final String MOBILES="['13888888888','13666666666']";
    //短信参数列表，用于依次填充模板，JSONArray 格式，每个变量长度不能超过 30 字,对于不包含变量的模板，不填此参数表示模板即短信全文内容
    private static final String PARAMS="['xxxx','xxxx']";

    public static void main(String[] args) throws Exception {

        DefaultHttpClient httpClient = new DefaultHttpClient();
        HttpPost httpPost = new HttpPost(SERVER_URL);
        String curTime = String.valueOf((new Date()).getTime() / 1000L);
        /*
         * 参考计算 CheckSum 的 java 代码，在上述文档的参数列表中，有 CheckSum 的计算文档示例
         */
        String checkSum = CheckSumBuilder.getCheckSum(APP_SECRET, NONCE, curTime);

        // 设置请求的 header
        httpPost.addHeader("AppKey", APP_KEY);
        httpPost.addHeader("Nonce", NONCE);
        httpPost.addHeader("CurTime", curTime);
        httpPost.addHeader("CheckSum", checkSum);
        httpPost.addHeader("Content-Type", "application/x-www-form-urlencoded;charset=utf-8");

        // 设置请求的的参数，requestBody 参数
        List<NameValuePair> nvps = new ArrayList<NameValuePair>();
        /*
         * 1.如果是模板短信，请注意参数 mobile 是有 s 的，详细参数配置请参考 **发送模板短信文档**
         * 2.参数格式是 jsonArray 的格式，例如 "['13888888888','13666666666']"
         * 3.params 是根据您模板里面有几个参数，那里面的参数也是 jsonArray 格式
         */
        nvps.add(new BasicNameValuePair("templateid", TEMPLATEID));
        nvps.add(new BasicNameValuePair("mobiles", MOBILES));
        nvps.add(new BasicNameValuePair("params", PARAMS));

        httpPost.setEntity(new UrlEncodedFormEntity(nvps, "utf-8"));

        // 执行请求
        HttpResponse response = httpClient.execute(httpPost);
        /*
         * 1.打印执行结果，打印结果一般会 200、315、403、404、413、414、500
         * 2.具体的 code 有问题的可以参考官网的 Code 状态表
         */
        System.out.println(EntityUtils.toString(response.getEntity(), "utf-8"));

    }
}
```
:::
::: code C#

```C#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Security.Cryptography;
using System.Net;
using System.IO;

namespace server_http_api
{
    class CheckSumBuilder
    {
        // 计算并获取 CheckSum
        public static String getCheckSum(String appSecret, String nonce, String curTime)
        {
            byte[] data = Encoding.Default.GetBytes(appSecret + nonce + curTime);
            byte[] result;

            SHA1 sha = new SHA1CryptoServiceProvider();
            // This is one implementation of the abstract class SHA1.
            result = sha.ComputeHash(data);

            return getFormattedText(result);
        }

        // 计算并获取 md5 值
        public static String getMD5(String requestBody)
        {
            if (requestBody == null)
                return null;

            // Create a new instance of the MD5CryptoServiceProvider object.
            MD5 md5Hasher = MD5.Create();

            // Convert the input string to a byte array and compute the hash.
            byte[] data = md5Hasher.ComputeHash(Encoding.Default.GetBytes(requestBody));

            // Create a new Stringbuilder to collect the bytes
            // and create a string.
            StringBuilder sBuilder = new StringBuilder();

            // Loop through each byte of the hashed data
            // and format each one as a hexadecimal string.
            for (int i = 0; i < data.Length; i++)
            {
                sBuilder.Append(data[i].ToString("x2"));
            }

            // Return the hexadecimal string.
            return getFormattedText(Encoding.Default.GetBytes(sBuilder.ToString()));
        }

        private static String getFormattedText(byte[] bytes)
        {
            char[] HEX_DIGITS = { '0', '1', '2', '3', '4', '5',
            '6', '7', '8', '9', 'a', 'b', 'c', 'd', 'e', 'f' };
            int len = bytes.Length;
            StringBuilder buf = new StringBuilder(len * 2);
            for (int j = 0; j < len; j++) {
                buf.Append(HEX_DIGITS[(bytes[j] >> 4) & 0x0f]);
                buf.Append(HEX_DIGITS[bytes[j] & 0x0f]);
            }
            return buf.ToString();
        }
    }

    class HttpClient
    {
        //发起 HTTP 请求
        public static void HttpPost(string url, Stream data, IDictionary<object, string> headers = null)
        {
            System.Net.WebRequest request = HttpWebRequest.Create(url);
            request.Method = "POST";
            if (data != null)
            request.ContentLength = data.Length;
            //request.ContentType = "application/x-www-form-urlencoded;charset=utf-8";

            if (headers != null)
            {
                foreach (var v in headers)
                {
                    if (v.Key is HttpRequestHeader)
                        request.Headers[(HttpRequestHeader)v.Key] = v.Value;
                    else
                        request.Headers[v.Key.ToString()] = v.Value;
                }
            }
            HttpWebResponse response = null;
            try
            {
                // Get the response.
                response = (HttpWebResponse)request.GetResponse();
                // Display the status.
                Console.WriteLine(response.StatusDescription);
                // Get the stream containing content returned by the server.
                Stream dataStream = response.GetResponseStream();
                // Open the stream using a StreamReader for easy access.
                StreamReader reader = new StreamReader(dataStream);
                // Read the content.
                string responseFromServer = reader.ReadToEnd();
                // Display the content.
                Console.WriteLine(responseFromServer);
                // Cleanup the streams and the response.
                reader.Close();
                dataStream.Close();
                response.Close();
            }
            catch (Exception e)
            {
                Console.WriteLine(e.Message);
                Console.WriteLine(response.StatusDescription);
            }
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            String url = "https://sms.yunxinapi.com/sms/sendtemplate.action";
            url += "?templateid=3030410&mobiles=['13888888888','13666666666']&params=['xxxx','xxxx']";//请输入正确的手机号

            //网易云信分配的账号，请替换您在网易云信控制台应用下创建的 Appkey
            String appKey = "fd460d34e786e7754e505bc4fab0f027";
            //网易云信分配的密钥，请替换您在网易云信控制台应用下创建的 appSecret
            String appSecret = "xxxxxxxx";
            //随机数（最大长度 128 个字符）
            String nonce = "12345";

            TimeSpan ts = DateTime.Now.ToUniversalTime() - new DateTime(1970, 1, 1);
            Int32 ticks = System.Convert.ToInt32(ts.TotalSeconds);
            //当前 UTC 时间戳，从 1970 年 1 月 1 日 0 点 0 分 0 秒开始到现在的秒数(String)
            String curTime = ticks.ToString();
            //SHA1(AppSecret + Nonce + CurTime),三个参数拼接的字符串，进行 SHA1 哈希计算，转化成 16 进制字符(String，小写)
            String checkSum = CheckSumBuilder.getCheckSum(appSecret, nonce, curTime);

            IDictionary<object, String> headers = new Dictionary<object, String>();
            headers["AppKey"] = appKey;
            headers["Nonce"] = nonce;
            headers["CurTime"] = curTime;
            headers["CheckSum"] = checkSum;
            headers["ContentType"] = "application/x-www-form-urlencoded;charset=utf-8";
            //执行 HTTP 请求
            HttpClient.HttpPost(url, null, headers);
        }
    }
}
```
:::
::: code Python

```Python
# coding=utf-8
import hashlib
import time
import requests
import json

def send_notice(mobiles,params):
    url = 'https://sms.yunxinapi.com/sms/sendtemplate.action'
    """
    AppKey    网易云信分配的账号，请替换您在网易云信控制台应用下创建的 Appkey
    Nonce    随机数（最大长度 128 个字符）
    CurTime    当前 UTC 时间戳，从 1970 年 1 月 1 日 0 点 0 分 0 秒开始到现在的秒数(String)
    CheckSum    SHA1(AppSecret + Nonce + CurTime)，三个参数拼接的字符串，进行 SHA1 哈希计算，转化成 16 进制字符(String，小写)
    """
    AppKey = ""
    # 生成 128 个长度以内的随机字符串
    nonce = hashlib.new('sha512', str(time.time()).encode("utf-8")).hexdigest()
    # 获取当前时间戳
    curtime = str(int(time.time()))
    # 网易云信的 App Secret
    AppSecret = ""
    # 根据要求进行 SHA1 哈希计算
    check_sum = hashlib.sha1((AppSecret + nonce + curtime).encode("utf-8")).hexdigest()

    header = {
        "AppKey": AppKey,
        "Nonce": nonce,
        "CurTime": curtime,
        "CheckSum": check_sum
    }

    data = {
        'mobiles': json.dumps(mobiles), # 手机号
        "templateid": 123456, # 模板 ID
        "params":json.dumps(params),

    }

    resp = requests.post(url, data=data, headers=header)

    print("Response:", resp.content)

if __name__ == '__main__':
    mobiles = ["12345678910", "12345678911"] # 要发送的手机号
    params = ["name","day"] # 模板中的变量
    send_notice(mobiles,params)
```
:::
::: code PHP

```PHP
<?php

/**
 * 网易云信 server API 简单实例
 * Class ServerAPI
 * @author chensheng dengyuan
 * @created date    2018-02-02 13:45
 *
 *
 ***/

class ServerAPI
{
    public $AppKey;                //网易云信控制台分配的 AppKey
    public $AppSecret;             //网易云信控制台分配的 AppSecret,可刷新
    public $Nonce;                    //随机数（最大长度 128 个字符）
    public $CurTime;                 //当前 UTC 时间戳，从 1970 年 1 月 1 日 0 点 0 分 0 秒开始到现在的秒数(String)
    public $CheckSum;                //SHA1(AppSecret + Nonce + CurTime),三个参数拼接的字符串，进行 SHA1 哈希计算，转化成 16 进制字符(String，小写)
    const HEX_DIGITS = "0123456789abcdef";

    /**
     * 参数初始化
     * @param $AppKey
     * @param $AppSecret
     * @param $RequestType [选择 php 请求方式，fsockopen 或 curl,若为 curl 方式，请检查 php 配置是否开启]
     */
    public function __construct($AppKey, $AppSecret, $RequestType = 'curl')
    {
        $this->AppKey = $AppKey;
        $this->AppSecret = $AppSecret;
        $this->RequestType = $RequestType;
    }

    /**
     * API checksum 校验生成
     * @param void
     * @return $CheckSum(对象私有属性)
     */
    public function checkSumBuilder()
    {
        //此部分生成随机字符串
        $hex_digits = self::HEX_DIGITS;
        $this->Nonce;
        for ($i = 0; $i < 128; $i++) {            //随机字符串最大 128 个字符，也可以小于该数
            $this->Nonce .= $hex_digits[rand(0, 15)];
        }
        $this->CurTime = (string)(time());    //当前时间戳，以秒为单位

        $join_string = $this->AppSecret . $this->Nonce . $this->CurTime;
        $this->CheckSum = sha1($join_string);
        //print_r($this->CheckSum);
    }

    /**
     * 将 json 字符串转化成 php 数组
     * @param $json_str
     * @return $json_arr
     */
    public function json_to_array($json_str)
    {

        if (is_array($json_str) || is_object($json_str)) {
            $json_str = $json_str;
        } else if (is_null(json_decode($json_str))) {
            $json_str = $json_str;
        } else {
            $json_str = strval($json_str);
            $json_str = json_decode($json_str, true);
        }
        $json_arr = array();
        foreach ($json_str as $k => $w) {
            if (is_object($w)) {
                $json_arr[$k] = $this->json_to_array($w); //判断类型是不是 object
            } else if (is_array($w)) {
                $json_arr[$k] = $this->json_to_array($w);
            } else {
                $json_arr[$k] = $w;
            }
        }
        return $json_arr;
    }

    /**
     * 使用 CURL 方式发送 post 请求
     * @param $url     [请求地址]
     * @param $data    [array 格式数据]
     * @return $请求返回结果(array)
     */
    public function postDataCurl($url, $data)
    {
        $this->checkSumBuilder();       //发送请求前需先生成 checkSum

        $timeout = 5000;
        $http_header = array(
            'AppKey:' . $this->AppKey,
            'Nonce:' . $this->Nonce,
            'CurTime:' . $this->CurTime,
            'CheckSum:' . $this->CheckSum,
            'Content-Type:application/x-www-form-urlencoded;charset=utf-8'
        );
        //print_r($http_header);

        // $postdata = '';
        $postdataArray = array();
        foreach ($data as $key => $value) {
            array_push($postdataArray, $key . '=' . urlencode($value));
        }
        $postdata = join('&', $postdataArray);

        // var_dump($postdata);

        $ch = curl_init();
        curl_setopt($ch, CURLOPT_URL, $url);
        curl_setopt($ch, CURLOPT_POST, 1);
        curl_setopt($ch, CURLOPT_POSTFIELDS, $postdata);
        curl_setopt($ch, CURLOPT_HEADER, false);
        curl_setopt($ch, CURLOPT_HTTPHEADER, $http_header);
        curl_setopt($ch, CURLOPT_SSL_VERIFYPEER, false); //处理 http 证书问题
        curl_setopt($ch, CURLOPT_CONNECTTIMEOUT, $timeout);
        curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);

        $result = curl_exec($ch);
        if (false === $result) {
            $result = curl_errno($ch);
        }
        curl_close($ch);
        return $this->json_to_array($result);
    }

    /**
     * 使用 FSOCKOPEN 方式发送 post 请求
     * @param $url     [请求地址]
     * @param $data    [array 格式数据]
     * @return $请求返回结果(array)
     */
    public function postDataFsockopen($url, $data)
    {
        $this->checkSumBuilder();//发送请求前需先生成 checkSum

        $postdata = '';
        foreach ($data as $key => $value) {
            $postdata .= ($key . '=' . urlencode($value) . '&');
        }
        // building POST-request:
        $URL_Info = parse_url($url);
        if (!isset($URL_Info["port"])) {
            $URL_Info["port"] = 80;
        }
        $request = '';
        $request .= "POST " . $URL_Info["path"] . " HTTP/1.1\r\n";
        $request .= "Host:" . $URL_Info["host"] . "\r\n";
        $request .= "Content-type: application/x-www-form-urlencoded;charset=utf-8\r\n";
        $request .= "Content-length: " . strlen($postdata) . "\r\n";
        $request .= "Connection: close\r\n";
        $request .= "AppKey: " . $this->AppKey . "\r\n";
        $request .= "Nonce: " . $this->Nonce . "\r\n";
        $request .= "CurTime: " . $this->CurTime . "\r\n";
        $request .= "CheckSum: " . $this->CheckSum . "\r\n";
        $request .= "\r\n";
        $request .= $postdata . "\r\n";

        print_r($request);
        $fp = fsockopen($URL_Info["host"], $URL_Info["port"]);
        fputs($fp, $request);
        $result = '';
        while (!feof($fp)) {
            $result .= fgets($fp, 128);
        }
        fclose($fp);

        $str_s = strpos($result, '{');
        $str_e = strrpos($result, '}');
        $str = substr($result, $str_s, $str_e - $str_s + 1);
        print_r($result);
        return $this->json_to_array($str);
    }

    /**
     * 发送模板短信
     * @param $templateid       [模板编号(由客服配置之后告知开发者)]
     * @param $mobiles          [验证码]
     * @param $params          [短信参数列表，用于依次填充模板，JSONArray 格式，如["xxx","yyy"];对于不包含变量的模板，不填此参数表示模板即短信全文内容]
     * @return $result      [返回 array 数组对象]
     */
    public function sendSMSTemplate($templateid, $mobiles = array(), $params = '')
    {
        $url = 'https://sms.yunxinapi.com/sms/sendtemplate.action';
        $data = array(
            'templateid' => $templateid,
            'mobiles' => json_encode($mobiles),
            'params' => json_encode($params)
        );
        if ($this->RequestType == 'curl') {
            $result = $this->postDataCurl($url, $data);
        } else {
            $result = $this->postDataFsockopen($url, $data);
        }
        return $result;
    }
}
?>
```
:::
::: code cURL
```cURL
curl -X POST -H "AppKey: go9dnk49bkd9jd9vmel1kglw0803mgq3" -H "CurTime: 1443592222" -H "CheckSum: 9e9db3b6c9abb2e1962cf3e6f7316fcc55583f86" -H "Nonce: 4tgggergigwow323t23t" -H "charset: utf-8" -H "Content-Type: application/x-www-form-urlencoded" -d 'templateid=1007&mobiles=["13812345678"]&params=["hello"]' 'https://sms.yunxinapi.com/sms/sendtemplate.action'
```
:::
::::::