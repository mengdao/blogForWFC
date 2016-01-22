---
layout: page
title: "实体-游记"
category: entity
date: 2015-04-08 11:17:04
---

# 游记
    Note

| 属性ID | 描述 | 数据类型 |
|-----|-----|-----|
|id   |游记id| string |
|ctime   |创建时间(unix时间戳，秒)| int |
|title   |标题| string |
|digest   |摘要| string |
|thumbnail   |缩略图url| string |
|num_visit   |浏览数量| int |
|num_comment   |评论数量| int |
|mdds   |归属[目的地]({% post_url 2015-04-08-entity-mdd %}#目的地)实体数组| array[entity] |
|user   |发布的[用户]({% post_url 2015-04-08-entity-user %}#用户)实体| entity |
|jump_url | 页面跳转的url | string |

