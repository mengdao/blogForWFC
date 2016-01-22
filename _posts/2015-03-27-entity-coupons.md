---
layout: page
title: "实体-优惠券"
category: entity
date: 2015-03-27 14:43:11
---

# 优惠劵
    Coupon

| 属性ID | 描述 | 数据类型 |
|-----|-----|-----|
|code	|优惠码|  string |
|price	|票面价格|  float  |
|title	|标题|  string |
|used_condition_price	|使用条件1：订单总价超过某价位，可以使用| float  |
|used_condition_sales_type	|使用条件2：规定某种类型的商品，可以使用| enum(int)  |
|used_condition_sales_id	|使用条件3：特定自由行商品id，可以使用| string  |
|used_condition_desc    |使用条件的描述|  string |
|valid_period	|有效期(unix时间戳)|  int |
|status	|优惠券状态(全部:0、可使用:1、已使用:2、已过期:3、退款(显示也是已使用):4)|  enum(int) |