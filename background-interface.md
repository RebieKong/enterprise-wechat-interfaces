## 后台接口

### 接口清单
- 用户管理接口
  - 新增用户接口
  - 修改用户信息接口
  - 获取用户信息接口
  - 新增组织接口
  - 修改组织接口
- 渠道管理接口
  - 增加渠道接口
  - 修改渠道接口
	
===============================

### 用户管理接口 

#### 获取单个用户信息接口
* PATH: `/admin/user/{user_id}`
* METHOD: `GET`
* 请求体

| 参数 | 参数名 |参数域| 是否必选 | 默认值 | 备注 | 
| ----- | ----- | ----- | ----- | ----- | ----- |
|user_id| 用户ID | path | `True` |||

* 返回体data域
```json
{
  "info": {
    "user_id": 123,
    "worker_name": "李",
    "worker_id": "007",
    "phone": "13101010101",
    "organization_id": "1"
  }
}
```
 [返回顶部](#接口清单)
 
#### 获取用户信息接口
* PATH: `/admin/user`
* METHOD: `GET`
* 请求体

| 参数 | 参数名 |参数域| 是否必选 | 默认值 | 备注 | 
| ----- | ----- | ----- | ----- | ----- | ----- |
|page| 页码 | query | `False` |1||
|page_size| 分页大小 | query | `False` |10||

* 返回体data域
```json
{
  "items": [
    {
      "user_id": 123,
      "worker_name": "李",
      "worker_id": "007",
      "phone": "13101010101",
      "organization_id": "1"
    }
  ],
  "pagination": {
    "current_page": 1,
    "item_size": 10,
    "total_size": 1000,
    "pages_size": 100
  }
}
```
 [返回顶部](#接口清单)
 
#### 新增用户接口
* PATH: `/admin/user/add`
* METHOD: `POST`
* 请求体

| 参数 | 参数名 |参数域| 是否必选 | 默认值 | 备注 | 
| ----- | ----- | ----- | ----- | ----- | ----- |
|worker_name| 姓名 | body | `True` |||
|worker_id| 工号 | body | `True` |||
|phone| 手机号码 | body | `True` |||
|organization_id| 组织ID | body | `True` |||

* 返回体data域
```json
{}
```
 [返回顶部](#接口清单)
 
#### 修改用户信息接口
* PATH: `/admin/user/{user_id}`
* METHOD: `PUT`
* 请求体

| 参数 | 参数名 |参数域| 是否必选 | 默认值 | 备注 | 
| ----- | ----- | ----- | ----- | ----- | ----- |
|user_id| 用户id | path | `True` |||
|worker_name| 姓名 | body | `False` |||
|worker_id| 工号 | body | `False` |||
|phone| 手机号码 | body | `False` |||
|organization_id| 组织ID | body | `False` |||

* 返回体data域
```json
{}
```
 [返回顶部](#接口清单)
