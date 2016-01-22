---
layout: page
title: "实体-用户"
category: entity
date: 2015-04-08 20:22:36
---

# 用户
    User

| 属性ID | 描述 | 数据类型 |
|-----|-----|-----|
|id   |用户id| string |
|name   |昵称| string |
|level   |用户级别| int |
|gender   |性别，未知:-1,女:0,男:1| enum(int) |
|logo   |头像缩略图的url| string |
|logo_600   |头像600宽度的url| string |
|logo_origin   |头像原图的url| string |
|intro   |签名| string |
|num_honey   |蜂蜜数量| int |
|m_bg_img   |移动背景图url| string |
|num_fans   |粉丝数| int |
|num_follows   |关注数| int |
|is_official   |是否官方账号| bool |
|qa_info   |[用户问答信息](#用户问答信息)| entity |
|poi_comment_info   |[用户点评信息](#用户点评信息)| entity |
|footprint_info   |[用户足迹信息](#用户足迹信息)| entity |
|jump_url | 页面跳转的url | string |

# 用户点评信息
    UserPOICommentInfo

| 属性ID | 描述 | 数据类型 |
|-----|-----|-----|
|num_poi_comments   |点评数| int |
|num_gold_poi_comments   |金牌点评数| int |


# 用户足迹信息
    UserFootprintInfo

| 属性ID | 描述 | 数据类型 |
|-----|-----|-----|
|state_num   |国家数| int |
|state_percent   |国家百分值(0-100)| int |
|city_num   |城市数| int |
|city_percent   |城市百分值(0-100)| int |
|foot_num   |足迹数| int |
|foot_percent   |足迹百分值(0-100)| int |

# 用户问答信息
    UserQAInfo

| 属性ID | 描述 | 数据类型 |
|-----|-----|-----|
|is_expert   |是否指路人| bool |

