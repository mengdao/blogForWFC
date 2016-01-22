---
layout: page
title: "实体-自由行相关"
category: entity
date: 2015-03-27 17:39:44
---

# 自由行-商品
    Sale

| 属性ID | 描述 |  数据类型 |
|-----|-----|-----|
|id   |商品编号| string  |
|title|标题| string  |
|type |商品类型| string |
|type_color |商品类型标记颜色| string |
|tag |标签| string |
|thumbnail |缩略图| string  |
|price_origin  |商品原价| float  |
|price_current  |商品现价| float  |
|discount |折扣描述| string |
|num_follows |浏览/关注数量| int |
|provider_name  |供应商名称| string |
|provider_tel   |供应商电话| string |
|category   |所选分类(数组形式，比如“6天5晚” “北京直飞” “希尔顿”)| array[string] |
|goods  |[自由行-货品](#自由行-货品)实体数组| array[entity] |
|mdds   |归属[目的地]({% post_url 2015-04-08-entity-mdd %}#目的地)实体数组| array[entity] |
|jump_url | 页面的url | string |

## 实现层的扩展字段
| 属性ID | 描述 |  数据类型 |
|-----|-----|-----|
|h5_url | 显示详情的h5的url | string |
|js_buy | 调用立即购买的js代码 | string |
|url_buy | 跳转立即购买的url | string |

    注：type的值包括: hotel, plane_hotel, plane, ship, rent, active, visa, local, ticket, other

# 自由行-货品
    SaleGood

| 属性ID | 描述 | 数据类型 |
|-----|-----|-----|
|id   |货品分类id| string |
|category   |所选分类(数组形式，比如“6天5晚” “北京直飞” “希尔顿”)| array[string] |
|price  |订单单价| float  |
|amount |订单中商品数目|  int |
|room_balance   |单房差金额|  float |
|room_amount    |房间数量| int  |

# 自由行-订单
    SaleOrder

| 属性ID | 描述 |  数据类型 |
|-----|-----|-----|
|id   |订单编号| string  |
|title  |标题| string  |
|sale   |[自由行-商品](#自由行-商品)实体| entity  |
|status |订单状态：未支付:1 已支付:2 正常关闭:3 超时关闭:4 定金已付款:5| enum(int)  |
|status_text| 订单状态文字| string|
|status_color| 订单状态颜色（#RRGGBB，‘#’开头）| string|
|total_fee  |支付金额| float |
|action_text| 行为按钮文字| string|
|action_fgcolor| 行为按钮前景状态颜色（#RRGGBB，‘#’开头）| string|
|action_bgcolor| 行为按钮背景状态颜色（#RRGGBB，‘#’开头）| string| 
|action_url | 根据不同状态做不同行为的url | string |
|jump_url | 页面跳转的url | string |

