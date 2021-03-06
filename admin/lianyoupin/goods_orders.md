# 兑换订单

## 兑换列表

`admin/order`

**请求方法**

`GET`

**请求参数**

`新增：currency增加eoc:cny:deduction EOC专区订单筛选`

|      名称       |  类型  | 默认 | 必须 |                                                   说明                                                    |
| :-------------: | :----: | :--: | :--: | :-------------------------------------------------------------------------------------------------------: |
|      limit      |  int   |  15  |  否  |                                                 每页条数                                                  |
|   goods_name    | string |  无  |  否  |                                                 商品名称                                                  |
| user_name_phone | string |  无  |  否  |                                             买家的姓名或电话                                              |
|  merchant_name  | string |  无  |  否  |                                                 商家姓名                                                  |
|  order_status   |  int   |  -1  |  否  | 订单状态:0-待付款 1-待发货 2-已发货 3-已完成 4-已退款 5-已退货 6-已关闭 7-商户订单退款中 8-商户订单已退款 |
|    order_no     | string |  无  |  否  |                                                  订单号                                                   |
|   start_time    | string |  无  |  否  |                                                 开始时间                                                  |
|    end_time     | string |  无  |  否  |                                                 结束时间                                                  |
|    currency     | string | comc |  否  |                      专区类型:comc-COMC 专区,ore-ORE 专区,eoc:cny:deduction-EOC 专区                      |
|    order_nos    | string |  无  |  否  |                                              订单号号(批量)                                               |

**SUCCESS 状态码**

`200`

**SUCCESS 返回体**

```json
{
  "current_page": 1,
  "data": [
    {
      "id": 1,
      "user_id": 1 /*用户ID*/,
      "goods_id": 1 /*商品ID*/,
      "merchant_id": 1 /*店铺ID*/,
      "order_id": 1,
      "goods_name": "商品名称" /*商品名称*/,
      "calculate": 100 /*算力*/,
      "ore": "1000.00000000" /*矿石奖励*/,
      "goods_image": 1 /*商品图片*/,
      "spec_type": 1 /*规格类型*/,
      "num": 1 /*数量*/,
      "goods_price": "1000.00000000" /*单价*/,
      "total_price": "1000.00000000" /*总价格*/,
      "specs_properties": "{}" /*sku集合*/,
      "extend": null,
      "remark": "备注" /*备注*/,
      "created_at": "2019-01-17 10:35:19" /*购买时间*/,
      "updated_at": "2019-01-17 10:35:21",
      "order_no": "E123123" /*订单号*/,
      "pay_price": "1000.00000000" /*支付金额*/,
      "express_id": 1 /*快递ID*/,
      "express_no": "运单号" /*运单号*/,
      "delivery_time": null /*发货时间*/,
      "receipt_time": null /*收货时间*/,
      "order_status": 1 /*订单状态: 0-等待付款 1-等待发货 2-已发货 3-已完成 4-已退款 5-已退货 6-已作废 7-商户订单退款中 8-商户订单已退款*/,
      "pay_type": "支付宝" /*支付类型*/,
      "currency": "comc" /*货币名称*/,
      "name": "T" /*用户名称*/,
      "phone": "18728624682" /*用户手机号*/,
      "consignee_name": null /*收货人名字*/,
      "consignee_phone": null /*收货人手机*/,
      "consignee_tag": null /*收货标签*/,
      "consignee_other": null /*收货其他信息*/,
      "consignee_area": null /*收货区域*/,
      "consignee_detail": null /*收货详情地址*/,
      "apply_refund_status": 1, // 申请退款状态 0-未申请 1-已申请 2-已驳回 3-已撤销 4-已完成
      "apply_refund_reason": "{
        // 申请退款原因
        'desc': '123', //
        'reason': '不想要了', // 申请退款原因
        'express_no': '2344', // 快递单号
        'express_code': 'jindong', // 快递公司编号
        'express_name': '京东', // 快递公司名称
        'refund_image': [], // 退款凭证
        'express_image': [] // 快递凭证
      }",
      "apply_refund_time": "2019-11-29 16:04:51", // 申请退款时间
      "reject_refund_reason": null, // 驳回退款原因
      "handle_refund_time": "2019-12-02 10:50:13", // 驳回退款时间
      "merchant_name": "商家" /*商家名称*/,
      "merchant_phone": "18781601158" /*商家电话*/,
      "merchant_avatar": "http://szl.qingchuanren.com/cacd83a7ac4ac6a2e173c0b5adf24c8e.png" /*商家头像*/
    }
  ],
  "first_page_url": "http://comc.com/admin/order?page=1",
  "from": 1,
  "last_page": 1,
  "last_page_url": "http://comc.com/admin/order?page=1",
  "next_page_url": null,
  "path": "http://comc.com/admin/order",
  "per_page": 15,
  "prev_page_url": null,
  "to": 1,
  "total": 1
}
```

## 发货

`admin/order/{goodsOrder}`

**请求方式**

`PUT`

**请求参数**

|    名称    |  类型  | 默认 | 必须 |  说明   |
| :--------: | :----: | :--: | :--: | :-----: |
| express_id |  int   |  无  |  是  | 快递 ID |
| express_no | string |  是  |  是  | 运单号  |

**SUCCESS 状态码**

`201`

**SUCCESS 返回体**

```json
{
  "message": "发货成功"
}
```

**ERROR 返回体**

```json
{
  "message": "请填写运单号"
}
```

## 修改物流信息

`admin/order/{itemOrder}/express`

**请求方式**

`PUT`

**请求参数**

|     名称     |  类型  | 默认 | 必须 |   说明   |
| :----------: | :----: | :--: | :--: | :------: |
| express_name | string |  无  |  是  | 快递名称 |
| express_code | string |  无  |  是  | 快递编号 |
|  express_no  | string |  是  |  是  |  运单号  |

**SUCCESS 状态码**

`201`

**SUCCESS 返回体**

```json
{
  "message": "发货成功"
}
```

**ERROR 返回体**

```json
{
  "message": "请填写运单号"
}
```

## 查看订单物流

`admin/order/{goodsOrder}/express`

**请求方法**

`GET`

**请求参数**

`无`

**返回体**

```json
[
  {
    "time": "2018-08-15 17:31:22",
    "context": "订单已由本人签收，感谢您在京东购物，欢迎您再次光临！"
  },
  {
    "time": "2018-08-15 15:43:02",
    "context": "配送员开始配送，请您准备收货，配送员，郑学超，手机号，13730834230或17360166072"
  },
  {
    "time": "2018-08-15 15:25:50",
    "context": "配送员开始配送，请您准备收货，配送员，郑学超，手机号，13730834230或17360166072"
  },
  {
    "time": "2018-08-15 15:04:27",
    "context": "货物已分配，等待配送"
  },
  {
    "time": "2018-08-15 12:53:05",
    "context": "货物已完成分拣，离开【成都郫县分拣中心】"
  },
  {
    "time": "2018-08-15 12:26:46",
    "context": "货物已到达【成都郫县分拣中心】"
  },
  {
    "time": "2018-08-15 12:26:46",
    "context": "货物已交付京东物流"
  }
]
```

## 取消订单

`admin/order/{goodsOrder}/cancel`

**请求方式**

`POST`

**请求参数**

|  名称  |  类型  | 默认 | 必须 |   说明   |
| :----: | :----: | :--: | :--: | :------: |
| reason | string |  无  |  是  | 取消原因 |

**SUCCESS 状态码**

`201`

**SUCCESS 返回体**

```json
{
  "message": "取消订单成功"
}
```

## 导出订单

`admin/order/export`

**请求方式**

`POST`

**请求参数**

|      名称       |  类型  | 默认 | 必须 |                                                   说明                                                    |
| :-------------: | :----: | :--: | :--: | :-------------------------------------------------------------------------------------------------------: |
|      limit      |  int   |  15  |  否  |                                                 每页条数                                                  |
|   goods_name    | string |  无  |  否  |                                                 商品名称                                                  |
| user_name_phone | string |  无  |  否  |                                             买家的姓名或电话                                              |
|  merchant_name  | string |  无  |  否  |                                                 商家姓名                                                  |
|  order_status   |  int   |  -1  |  否  | 订单状态:0-待付款 1-待发货 2-已发货 3-已完成 4-已退款 5-已退货 6-已关闭 7-商户订单退款中 8-商户订单已退款 |
|    order_no     | string |  无  |  否  |                                                  订单号                                                   |
|   start_time    | string |  无  |  否  |                                                 开始时间                                                  |
|    end_time     | string |  无  |  否  |                                                 结束时间                                                  |
|    currency     | string | comc |  否  |                                             货币类型 comc,ore                                             |
|    order_nos    | string |  无  |  否  |                                              订单号号(批量)                                               |

**SUCCESS 状态码**

`201`

**SUCCESS 返回体**

```json
{
  "download_url": "http://comc.com/storage/2019-04-29-现金区订单导出.xlsx"
}
```

## 驳回退货

`admin/order/{orderId}/agree/refund`

**请求方式**

`POST`

**请求参数**

|  名称  |  类型  | 默认 | 必须 |   说明   |
| :----: | :----: | :--: | :--: | :------: |
| reason | string |  无  |  是  | 驳回原因 |

**SUCCESS 状态码**

`201`

**SUCCESS 返回体**

```json
{
  "message": "驳回成功"
}
```

## 同意退货

`admin/order/{orderId}/reject/refund`

**请求方式**

`POST`

无

**SUCCESS 状态码**

`201`

**SUCCESS 返回体**

```json
{
  "message": "操作成功"
}
```
