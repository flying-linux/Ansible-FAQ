### 如何调用DMK的API\(https\)

#### 1. Token获取的API：

* ##### POST [https://x.x.x.x:8443/api/v1/users/get\_token](http://x.x.x.x:8443/api/v1/users/get_token)
* ##### body参数：{"username" =&gt; "apicaller", "password" =&gt; "Huawei@123"}

![](/assets/get_token.png)

#### 2. Token获取完成后，其他API调用：

调用用其他API需要在请求header传入tocken，自定义键为**TOKENID**，值为获取到的token值。

##### 请求举例：

![](/assets/token_id.png)

### API接口文档

[IMFACE的接口管理系统查看](http://intetool-imface.huawei.com/#!/products/adefb0a3-d15f-49b7-922d-fe3ab32aea22?solution_id=4a8dd01c-0af4-4395-a8c5-aa7a69e23493&serviceFlag=false)

