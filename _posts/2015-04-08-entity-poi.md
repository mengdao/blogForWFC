---
layout: page
title: "实体-POI"
category: entity
date: 2015-04-08 11:16:59
---

# POI
    POI

| 属性ID | 描述 | 数据类型 |
|-----|-----|-----|
|id   |POI id| string |
|name   |名称| string |
|foreign_name   |外语名称| string |
|rank   |评级 0-5| int |
|price   |消费价格| float |
|price_type   |消费价格单位(货币符号)| string |
|type_id   |类型| enum(int) |
|thumbnail   |缩略图url| string |
|tags | [标签](#POI标签)实体（如：3星级，经济型） | array[entity] |
|num_comment   |点评数量| int |
|num_travelnote   |相关游记数量| int |
|num_footprint   |标记足迹(到过/去过)的数量| int |
|lat   |纬度，6位小数| double |
|lng   |经度，6位小数| double |
|mdd   |归属[目的地]({% post_url 2015-04-08-entity-mdd %}#目的地)实体| entity |
|area |归属[目的地区域]({% post_url 2015-04-08-entity-mdd %}#目的地区域)实体| entity |
|district |归属[目的地行政区]({% post_url 2015-04-08-entity-mdd %}#目的地行政区)实体| entity |
|honors   |荣耀列表| array[[POI荣耀](#POI荣耀)] |
|jump_url | 页面跳转的url | string |
|comments | POI点评列表 | array[[POI点评](#POI点评)实体] |


# 酒店:POI
    Hotel

| 属性ID | 描述 | 数据类型 |
|-----|-----|-----|
|hotel_jump_url | 酒店页面的特定跳转url | string |


# POI荣耀
    POIHonor

| 属性ID | 描述 | 数据类型 |
|-----|-----|-----|
|title | 荣耀名称 | string |
|s_icon_url | 荣耀小图标url | string |

# POI标签
    POITag

| 属性ID | 描述 | 数据类型 |
|-----|-----|-----|
|id | 标签id | string |
|name | 标签名称 | string |


# POI点评
    POIComment

| 属性ID | 描述 | 数据类型 |
|-----|-----|-----|
|id   |点评id| string |
|comment   |点评内容| string |
|poi   |所属[POI](#poi)实体| entity |
|price   |平均消费| float |
|rank   |评级 0-5| int |
|sub_ranks |子评星字典| dictionary(rank_${子评级名称key}->int(点评等级(0-5)) |
|ctime   |创建时间(unix时间戳，秒)| int |
|mtime   |修改时间(unix时间戳，秒)| int |
|is_gold| 是否金牌点评|bool(0/1)|
|note   |关联[游记]({% post_url 2015-04-08-entity-note %}#游记)实体| entity |
|images   |点评[图片]({% post_url 2015-04-08-entity-image %})实体数组| array[entity] |
|owner   |发布的[用户]({% post_url 2015-04-08-entity-user %}#用户)实体| entity |

注：子评星映射表 (php代码：type_id -> 结构(参数->(服务器的key，显示名字)))

```
        '1' => array( // 美食
            'rank_taste'=>array('key'=>'taste_rank','name'=>'口味'),
            'rank_env'=>array('key'=>'env_rank','name'=>'环境'),
            'rank_service'=>array('key'=>'service_rank','name'=>'服务'),
        ),
        '2' => array( // 住宿
            'rank_service'=>array('key'=>'service_rank','name'=>'服务'),
            'rank_fair'=>array('key'=>'fair_rank','name'=>'性价比'),
            'rank_clean'=>array('key'=>'clean_rank','name'=>'卫生'),
        ),
        '3' => array( // 景点
            'rank_scene'=>array('key'=>'scene_rank','name'=>'风光'),
            'rank_feature'=>array('key'=>'feature_rank','name'=>'当地特色'),
            'rank_service'=>array('key'=>'service_rank','name'=>'公共服务'),
        ),
```


