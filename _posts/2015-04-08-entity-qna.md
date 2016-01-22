---
layout: page
title: "实体-问答"
category: entity
date: 2015-04-08 11:24:24
---

# 问题
    Question

| 属性ID | 描述 | 数据类型 |
|-----|-----|-----|
|id   |问题id| string |
|title   |标题| string |
|content   |内容| string |
|ctime   |创建时间(unix时间戳，秒)| int |
|mdd   |归属[目的地]({% post_url 2015-04-08-entity-mdd %}#目的地)实体| entity |
|num_answer   |回答数量| int |
|jump_url | 页面跳转的url | string |
|user   |发布的[用户]({% post_url 2015-04-08-entity-user %}#用户)实体| entity |


# 回答
    QuestionAnswer

| 属性ID | 描述 | 数据类型 |
|-----|-----|-----|
|id   |回答id| string |
|question   |回答的[问题](#问题)实体| entity |
|content   |回答内容| string |
|ctime   |创建时间(unix时间戳，秒)| int |
|user   |回答的[用户]({% post_url 2015-04-08-entity-user %}#用户)实体| entity |





