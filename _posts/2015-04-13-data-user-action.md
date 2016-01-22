---
layout: page
title: "用户行为"
category: data
date: 2015-04-13 12:18:42
---

# 用户行为接口 
- mapi.mafengwo.cn/travelguide/useraction/

## 当前用户在某目的地下的浏览记录
- 请求URL：pv/mine/mdds/{mdd_id}

- 请求方式：GET

- 约束条件：

- 请求参数：

- 返回数据：最多半年内的数据 且 不超过100条，不分页一次返回（暂且这样，有问题找陈惠）
    + type字段的值：
        * 目的地/景点/美食/购物/娱乐/酒店/游记榜单/问答/自由行
    + jump_url的链接页面：
        * 【目的地】目的地页
        * 【景点/美食/购物/娱乐/酒店】POI详情页
        * 【榜单】POI榜单详情页
        * 【攻略】攻略详情页页
        * 【游记】游记详情页
        * 【问答】问题详情页
        * 【自由行】自由行详情页

- 相关实体：无

```
{
    list = [
                {
                    name: // 历史浏览的内容的名称, string
                    type: // 该内容的类型描述（中文类型描述，见上面描述）, string
                    entity_id: // 当前记录的关联实体的id, string
                    jump_url: // 该推内容的跳转sharejump或url, string
                },
                ...
    ]
}
```
    
