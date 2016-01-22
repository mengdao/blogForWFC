---
layout: page
title: "Widget"
category: data
date: 2015-04-08 12:29:43
---

# Widget接口 
- mapi.mafengwo.cn/travelguide/widget/

## 当地
### 获取某个目的地下的Widget的种类信息
- 请求URL：config/mdds/{mdd_id}/local

- 请求方式：GET

- 约束条件：

- 请求参数： 
    + *c_lat* : 当前位置的纬度，6位小数, float
    + *c_lng* : 当前位置的经度，6位小数, float

- 返回数据：
    * Widget的种类结果列表，不同widget独立[加载数据](#不同Widget在指定目的地下的数据)
    * 'history'类型的widget数据做本地存储，仅在首次用户访问这个目的地，没有数据时用[这个]({% post_url 2015-04-13-data-user-action %}#当前用户在某目的地下的浏览记录)接口同步服务器
- 相关实体：无

```
{
    mdd = { <<目的地>>, 指定的目的地
        id: // 目的地id, string
        name: // 目的地名称, string
        lat: // 纬度，6位小数, double
        lng: // 经度，6位小数, double
    },
    list = [
                {   
                    id: // widget id
                    title: // widget名称 
                    type: // widget的类型（history, nearby, hotels, features, sales）

                    has_more: // 是否显示查看更多xxx, bool
                    more_text: // 查看更多的文字描述, string
                    more_jump_url: // 点击查看更多的sharejump或url链接, string
                },
                ...
    ]
}
```


## Widget相关
### 不同Widget在指定目的地下的数据 
- 请求URL：{widget_id}/data/mdds/{mdd_id}

- 请求方式：GET

- 约束条件：
    + 支持widget类型: history, nearby, hotels, features, sales

- 请求参数：
    + *c_lat* : 当前位置的纬度，6位小数, float
    + *c_lng* : 当前位置的经度，6位小数, float
    
- 返回数据 (type: hotels)：{widget_id} 对应的 type 为 "hotels" 时的返回结果
    + 相关实体：
        - [目的地区域]({% post_url 2015-04-08-entity-mdd %}#目的地区域)

```
{
    num_hotels: // 该目的地的酒店数量, int
    list = [
                {
                    title: 推荐项的名称
                    choise_ratio: // 该推荐项的选择度 0.0 - 1.0 , float
                    area: { 推荐项所在的<<目的地区域>>
                        id: // 区域id, string
                        name: // 区域名称, string
                    }
                    jump_url: // 该推荐项的跳转sharejump或url, string
                },
                ...
    ]
}
```

- 返回数据 (type: features)：{widget_id} 对应的 type 为 "features" 时的返回结果
    + 相关实体：无

```
{
    list = [
                {
                    title: // 特色标题, string
                    count: // 该条特色涉及的数字, int, (如果小于0则不显示数字，只显示suffix描述)
                    suffix: // 该条特色涉及的数字描述, string
                    icon: // 特色图标, string
                    jump_url: // 该推特色内容的跳转sharejump或url, string
                },
                ...
    ]
}
```

- 返回数据 (type: sales)：{widget_id} 对应的 type 为 "sales" 时的返回结果
    + 相关实体：
        - [自由行-商品]({% post_url 2015-03-27-entity-sale %}#自由行-商品)

```
{
    list = [
                { <<自由行-商品>>
                    id: // 商品编号, string
                    title: // 标题, string
                    thumbnail: // 缩略图, string
                    price_origin: // 商品原价, float
                    price_current: // 商品现价, float
                    discount: // 折扣描述, string
                    num_follows: // 关注数量, int
                    jump_url: // 页面的url , string
                },
                ...
    ]
}
```