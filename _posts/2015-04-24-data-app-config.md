---
layout: page
title: "App配置相关"
category: data
date: 2015-04-24 17:55:31
---

# 配置接口
- mapi.mafengwo.cn/travelguide/config/

## 获取App全局配置
- 请求URL：
    + global

- 请求方式：GET

- 约束条件：

- 请求参数： 
    + *c_lat* : 当前位置的纬度，6位小数, float
    + *c_lng* : 当前位置的经度，6位小数, float

- 返回数据：全局配置(所有配置项定义如下，配置可能根据用户地区做不同配置)

```
{
    type = global, // string
    hotel_grades = { // 实用平台iphone, ipad, android
        key: // 选项key(用于接口传输参数的值), string
        name: // 选项名称(用于显示), string
    },
}
```


