---
layout: page
title: "优惠券"
category: data
date: 2015-03-27 10:42:04
---

# 优惠劵接口 
- mapi.mafengwo.cn/travelguide/coupon/

## 获取我的优惠劵
- 请求URL：coupons/mine

- 请求方式：GET

- 约束条件：必须登录

- 请求参数： 
    + *start*: 下一页起始位置，使用返回数据的offset，string
    + *length*: 该次取列表数据的长度
    
- 返回数据：优惠劵列表
- 相关实体：
    + [优惠券]({% post_url 2015-03-27-entity-coupons %}#优惠券)

```
{
    offset = "xxx", 服务器指定结束位置偏移量
    has_more = 0:没有更多，1:还有更多,
    list = [
                {   <<优惠券>>
                    code: // 优惠码，string
                    price: // 票面价格，int
                    title: // 标题，string
                    used_condition_desc: // 使用条件的描述，string
                    valid_period: // 使用有效期，unix时间戳，int
                    status: // 优惠券状态(全部:0、可使用:1、已使用:2、已过期:3、退款(显示为已使用):4)，enum(int)
                    color: // 颜色描述，格式:#AARRGGBB, string
                },
                ...
    ]
}
```

- 备注：


## 添加我的优惠劵
- 请求URL：add_code

- 请求方式：POST

- 约束条件：必须登录

- 请求参数： 
    + *code*(必传): 优惠码，string
    
- 返回数据：
    + 成功: 
        ```
        {
            result = 1
        }
        ```
    + 失败: 通过rc和rm

- 备注：

## 添加我的优惠劵(小米卡包)
- 请求URL：add_xiaomi_code

- 请求方式：POST

- 约束条件：必须登录

- 请求参数： 
    + *code*(必传): 优惠码，string
    注：将小米卡包其他的参数一并传过来，并加个前缀‘xm_’前缀
    
- 返回数据：
    + 成功: 
        ```
        {
            result = 1
        }
        ```
    + 失败: 通过rc和rm

- 备注：



