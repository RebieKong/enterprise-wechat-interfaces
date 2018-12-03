## H5接口

### 接口清单
- 工单接口
    - [工单列表接口](#列表接口)
    - [工单详情接口](#详情接口)
    - [获取接触原因接口](#获取接触原因接口)
    - [增加接触信息接口](#增加接触信息接口)
    - [获取转单人接口](#获取转单人接口)
    - [发起转单接口](#发起转单接口)
    - [发起回单接口](#发起回单接口)
	
===============================

### 工单接口
#### 列表接口
* PATH: `/active-job`
* METHOD: `GET`
* 请求体

| 参数 | 参数名 |参数域| 是否必选 | 默认值 | 备注 | 
| ----- | ----- | ----- | ----- | ----- | ----- |
|search| 搜索内容 | query | `False` |`null`||
|order-status| 工单状态 | query | `False` |0||
|contact-status| 客户意愿 | query  | `False` |0||
|page| 页码 | query  | `False` | 1 ||
|page-size| 分页 | query  | `False` | 10 ||

* 返回体data域
```json
{
  "items": [
    {
      "order_id": "1234567",
      "activity_name": "宽进融",
      "status": 1,
      "order_create_time": "2018-01-01 00:00:00",
      "lastest_contact": {
        "contact_time": "2018-01-01 00:00:00",
        "status": 1,
        "status_reason": "",
        "status_remark": ""
      }
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

#### 详情接口
* PATH: `/active-job/{order_id}`
* METHOD: `GET`
* 请求体

| 参数 | 参数名 |参数域| 是否必选 | 默认值 | 备注 | 
| ----- | ----- | ----- | ----- | ----- | ----- |
|order_id| 工单编号 | path | `True` |||

* 返回体data域
```json
{
  "customer_info": {
    "customer_name": "fsample",
    "customer_type": "客户",
    "phone": "10000",
    "mobile": "199999999",
    "broadband_account": "",
    "email": "aa@10000.com",
    "qq": "1"
  },
  "order_status": 1,
  "activity_info": {
    "activity_name": "宽进融",
    "activity_start_time": "2018-01-01 00:00:00",
    "activity_end_time": "2019-01-01 00:00:00",
    "products": [
      {
        "product_name": "产品名1",
        "stage": "主推"
      },
      {
        "product_name": "产品名2",
        "stage": "次推"
      },
      {
        "product_name": "产品名3",
        "stage": "顺推"
      }
    ],
    "talking_skill": "balabala how are you"
  },
  "retrieve_info": {
    "worker": "李小龙",
    "retrieve_time": "2018-01-01 00:00:00",
    "type": 1
  },
  "contact_log": [
    {
      "contact_time": "2018-01-01 00:00:00",
      "status": 1,
      "status_reason": "",
      "status_remark": ""
    }
  ],
  "order_log": [
    {
      "worker_name": "龙小李",
      "type": 1,
      "act_time": "2018-01-01 00:00:00"
    }
  ],
  "marketing_info": {
    "some_key_in_chinese1": "some value",
    "some_key_in_chinese2": "some value"
  }
}
```
 [返回顶部](#接口清单)
 
#### 获取接触原因接口
* PATH: `/active-job/contact-reason`
* METHOD: `GET`

* 返回体data域
```json
{
  "contact_reason": [
    {
      "status": "1",
      "reason": [
        "r1",
        "r2"
      ]
    },
    {
      "status": "2",
      "reason": [
        "r3",
        "r4"
      ]
    }
  ]
}
```
 [返回顶部](#接口清单)
 
#### 增加接触信息接口
* PATH: `/active-job/contact/{order_id}`
* METHOD: `PUT`
* 请求体

| 参数 | 参数名 |参数域| 是否必选 | 默认值 | 备注 | 
| ----- | ----- | ----- | ----- | ----- | ----- |
|order_id| 工单编号 | path | `True` |||
|contact_status| 接触结果 | query | `True` |||
|contact_status_reason| 接触结果原因 | query | `False` |||
|contact_status_remark| 接触结果备注 | query | `False` |||

* 返回体data域
```json
{}
```
 [返回顶部](#接口清单)
 
#### 获取转单人接口
* PATH: `/active-job/shipping/worker-list`
* METHOD: `GET`
* 请求体

* 返回体data域
```json
{
  "workers": [
    {
      "worker_name": "李小芳",
      "worker_id": "1",
      "type": 1
    }
  ]
}
```
 [返回顶部](#接口清单)
 
#### 发起转单接口
* PATH: `/active-job/shipping/${order_id}`
* METHOD: `POST`
* 请求体

| 参数 | 参数名 |参数域| 是否必选 | 默认值 | 备注 | 
| ----- | ----- | ----- | ----- | ----- | ----- |
|order_id| 工单编号 | path | `True` |||
|worker_id| 转单人ID | body | `True` |||

* 返回体data域
```json
{}
```
 [返回顶部](#接口清单)
 
#### 发起回单接口
* PATH: `/active-job/retrieve/${order_id}`
* METHOD: `POST`
* 请求体

| 参数 | 参数名 |参数域| 是否必选 | 默认值 | 备注 | 
| ----- | ----- | ----- | ----- | ----- | ----- |
|order_id| 工单编号 | path | `True` |||
|retrieve_info| 回单信息 | body | `True` |||

* 返回体data域
```json
{}
```
 [返回顶部](#接口清单)
 
