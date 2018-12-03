## 公共部分
### 公共接口

#### 登陆接口
* PATH: `/user/login`
* METHOD: `POST`
* 请求体(不服从公共请求)

| 参数 | 参数名 |参数域| 是否必选 | 默认值 | 备注 | 
| ----- | ----- | ----- | ----- | ----- | ----- |
|open_id| 微信OPENID | body | `True` |||

* 返回体data域  
```json
{
    "token":"",
    "expired_time":"2018-01-01 00:00:00"
}
```
#### 更新token接口
* PATH: `/user/update-token`
* METHOD: `POST`
* 请求体(服从公共请求)

| 参数 | 参数名 |参数域| 是否必选 | 默认值 | 备注 | 
| ----- | ----- | ----- | ----- | ----- | ----- |

* 返回体data域  

```json
{
    "token":"",
    "expired_time":"2018-01-01 00:00:00"
}
```


### 公共请求体
所有请求在query中添加token，即：
```
request:
/user/update-token
===>
/user/update-token?token=this is token
```

### 公共返回体
```json
{
    "status":"",
    "msg":"",
    "token_status":1,
    "data":{}
}
```

| 状态码 | 含义 | 解决方案 |
|-----|-----|-----|
|0|正常|| 
|-1| token已过期或token错误|重新登陆或刷新token|
|-2| 权限不足 | 重新检查接口文档 |
|-3| 路径不存在 | 重新检查接口文档 |
|-4| 接口数据缺失 | 重新检查接口文档 |

| token_status |
|-----|
|0|正常|| 
|1| token即将过期|
