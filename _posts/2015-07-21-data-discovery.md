---
layout: page
title: "发现"
category: data
date: 2015-07-20 18:36:04
---

# 发现接口 
- mapi.mafengwo.cn/travelguide/discovery/

## 获取发现首页
- 请求URL：home

- 请求方式：GET

- 约束条件：

- 请求参数：

- 相关实体：

- 返回数据：
    + 支持如下注1的全部几种样式，顺序根据后台控制

```
{
    list = [
        {
            title: // 标题(支持富文本), string
            sub_title: // 副标题(支持富文本)，可以为空, string
            style: // 样式id, string
            jump_url: // 点击标题所跳转的h5或sharejump, string
            list: [
                {
                    ... 不同样式下的结构字段不同，如下注1
                },
                ...
            ]
        },
        ...
    ]
}
```

- 注1：style样式字段共包括以下几种：

- discovery_entrance（发现四个饼部分）

```
{
    title: // 标题, string
    icon: // 图标url, string
    jump_url: // 跳转的h5或sharejump, string
}
```

- 3_squares

```
{
    title: // 标题(支持富文本), string
    sub_title: // 副标题(支持富文本), string
    img_url: // 方块图片url, string
    jump_url: // 跳转的h5或sharejump, string
}
```

- 6_squares

```
{
    title: // 标题(支持富文本), string
    sub_title: // 副标题(支持富文本), string
    img_url: // 方块图片url, string
    jump_url: // 跳转的h5或sharejump, string
}
```

- sales

```
{ <<自由行-商品>>
    id: // 商品编号, string
    title: // 标题, string
    type: // 商品类型, string
    thumbnail: // 缩略图, string
    price_current: // 商品现价, float
    price_suffix: // 价格后面的文字, string
    num_follows: // 关注数量, int
    mdd_name: // 目的地名称， string
    jump_url: // 跳转的h5或sharejump, string
}
```

- notes

```
{ <<游记>>
    id: // 游记id, string
    title: // 标题, string
    thumbnail: // 缩略图url, string
    num_comment: // 浏览数量, int
    user: { // <<用户>>实体, entity
        id: // 用户id, string
        name: // 昵称, string
        logo: // 头像缩略图的url, string
    }
    jump_url: // 跳转的h5或sharejump, string
}
```

- horizontal_scroll

```
{
    img: // 图片url, string
    jump_url: // 跳转的h5或sharejump, string
}
```

- plays

```
{
    title: // 标题(支持富文本), string
    desc: // 描述(支持富文本), string
    img_url: // 图片url, string
    badge_icon: // badge的图标icon的url, string
    jump_url: // 跳转的h5或sharejump, string
}
```


## 获取发现专题内容列表
- 请求URL：topics

- 请求方式：GET

- 约束条件：

- 请求参数：
    + id(必传): // 专题id，string
    + style(必传): // 专题样式，string
    + *start*: 下一页起始位置，使用返回数据的offset，string
    + *length*: 该次取列表数据的长度, int

- 相关实体：

- 返回数据：
    + 支持如下几种样式，通过style区别对待，支持翻页:
        - "square"
        - "sales"
        - "notes"
        - "tops_list"

```
{
    offset = "xxx", 服务器指定结束位置偏移量
    has_more = 0:没有更多，1:还有更多,
    list: [
        {
            
        },
        ...
    ]
}
```


## 获取发现换个玩法
- 请求URL：any_play

- 请求方式：GET

- 约束条件：

- 请求参数：

- 相关实体：

- 返回数据：


```
{
    title: // 标题(支持富文本), string
    desc: // 描述(支持富文本), string
    badge_icon: // badge的图标icon的url, string
    jump_url: // 跳转的h5或sharejump, string
}
```