---
layout: page
title: "实体-攻略"
category: entity
date: 2015-04-08 21:07:45
---

# 结构化攻略
    Book

| 属性ID | 描述 | 数据类型 |
|-----|-----|-----|
|id   |攻略id| string  |
|title   |标题| string |
|subtitle   |子标题| string |
|mddid  | 目的地id | string |
|mddname | 目的地名称 | string |
|mdd   |所属[目的地]({% post_url 2015-04-08-entity-mdd %}#目的地)实体| entity |
|cover   |封面缩略图url| string |
|utime   |更新时间(unix时间戳，秒)| int |
|file   |攻略下来url| string |
|size   |攻略大小(单位:字节)| long long |
|catalog_online|在线攻略结构| JSON object |
|ver   |攻略版本号| string |
|geo   |地理位置的名称数组| array[string] |
|unique   |特色描述词数组| array[string] |
|jump_url | 页面跳转的url | string |

