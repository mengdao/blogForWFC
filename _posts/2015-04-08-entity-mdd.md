---
layout: page
title: "实体-目的地"
category: entity
date: 2015-04-08 11:17:14
---

# 目的地
    Mdd

| 属性ID | 描述 | 数据类型 |
|-----|-----|-----|
|id   |目的地id| string  |
|name   |目的地名称| string |
|foreign_name   |目的地外语名称| string |
|pinyin   |目的地名称的拼音| string |
|lat   |纬度，6位小数| double |
|lng   |经度，6位小数| double |
|parent   |父级[目的地](#目的地)实体| entity |
|thumbnail   |缩略图url| string |
|header_img   |头图url| string |
|is_country   |是否为国家| bool |
|num_have_been |多少蜂蜂去过的数| int |
|num_want_go   |多少蜂蜂想去的数| int |
|jump_url | 页面跳转的url | string |


# 目的地区域
    MddArea

| 属性ID | 描述 | 数据类型 |
|-----|-----|-----|
|id   |区域id| string  |
|name   |区域名称| string |
|choice_percent | 选择百分比 | float(0.0 - 1.0)|
|num_pois|区域内的poi数| int |
|region_gps|区域gps顺时针或逆时针的顺序数组|array[object(lat=>,lng=>)]|

# 目的地行政区
    MddDistrict

| 属性ID | 描述 | 数据类型 |
|-----|-----|-----|
|id   |行政区id| string  |
|name   |行政区名称| string |

