---
layout: page
title: "酒店"
category: data
date: 2015-06-18 18:56:32
---

# 酒店接口
- mapi.mafengwo.cn/travelguide/hotel/

## 获取目的地酒店列表
- 请求URL：
    + hotels/mdds/{mdd_id}
    + hotels/mdds/{mdd_id}/areas/{area_id}
    + {poi_id}/around_hotels/mdds/{mdd_id}
    + hotels/around_me/mdds/{mdd_id}

- 请求方式：GET

- 约束条件：

- 请求参数：
    + *start*: 下一页起始位置，使用返回数据的offset，string
    + *length*: 该次取列表数据的长度, int

    + 筛选参数（四个接口各自参数）：
        - hotels/mdds/{mdd_id}：
            + 不需要特定参数
        - hotels/mdds/{mdd_id}/areas/{area_id}：
            + 不需要特定参数
        - {poi_id}/around_hotels：
            + 不需要特定参数
        - hotels/around_me：
            + *radius_type*: 半径范围（radius_type中的key），如果不传，则服务器随便定义一个默认值
        
        - 通用筛选参数（任何上述优先级都支持的参数）：
            + *keyword* : // 关键词, string 
            + *grade_type*: // 酒店级别（从通用配置中获取）, string
            + *check_in* : // 入住时间(格式：yyyy-MM-dd), string 
            + *check_out* : // 退房时间(格式：yyyy-MM-dd), string 
            + *has_room* : // 是否有房, bool(0/1)
            + *sort_type*: 排序类型（sort_type中的key），不传服务器定义默认排序方式
            + *price_low*: 价格范围，最低价，（price_type中的low），不传表示不限制
            + *price_high*: 价格范围，最高价，（price_type中的high），不传表示不限制
    
- 返回数据：酒店列表
- 相关实体：
    + [酒店:POI]({% post_url 2015-04-08-entity-poi %}#酒店:POI)
    + [POI点评]({% post_url 2015-04-08-entity-poi %}#POI点评)
    + [目的地区域]({% post_url 2015-04-08-entity-mdd %}#目的地区域)

```
{
    offset = "xxx", 服务器指定结束位置偏移量
    has_more = 0:没有更多，1:还有更多,
    list = [
        { <<POI:酒店>>实体
            id: // POI id, string
            name: // 名称, string
            foreign_name: // 外语名称, string
            rank: // 评级 0-5, int
            price: // 消费价格, float
            price_type: // 消费价格单位(货币符号), string
            type_id: // 类型, enum(int)
            thumbnail: // 缩略图url, string
            tags: [ // <<POI标签>>实体数组, array[entity]
                {
                    id: // POI标签id, string
                    name: // POI标签名称, string
                },
                ... 
            ]
            num_comment: // 点评数量, int
            lat: // 纬度，6位小数, double
            lng: // 经度，6位小数, double
            area: { // <<目的地区域>>实体
                id: // 区域id, string
                name: // 区域名称, string
            }
            district: { // <<目的地行政区>>实体
                id: // 行政区id, string
                name: // 行政区名称, string
            }
            honors = [ 
                { // <<POI荣耀>>实体
                    title: // 荣耀名称, string
                    s_icon_url: // 荣耀小图标url, string
                },
                ...
            ], 
            comments = [ // 该接口现在只返回一条点评数据，但依旧使用数组形式，以保证实体本身的能力和可扩展性，该条点评根据需求返回（如：top或编辑推荐的第一个之类的xx）
                { // <<POI点评>>实体
                    id: // 点评id, string
                    comment: // 点评内容, string
                    rank: // 评级 0-5, int
                    owner: { // <<用户实体>>, entity
                        id: // 用户id, string
                        name: // 昵称, string
                        logo: // 头像缩略图的url, string
                    }
                }, ...
            ]

            // 下面不属于实体属性字段
            thumbnail_mask = "http://groupinfo.w180s.jpeg”,
        },
        ...
    ],
}
```

- 备注：

## 获取目的地酒店筛选列表
- 请求URL：
    + filters/mdds/{mdd_id}

- 请求方式：GET

- 约束条件：

- 请求参数：
    + *type_id*(必传): poi类型（要求: 非酒店类型的type_id）， enum(int)
    
- 返回数据：poi筛选项列表
- 相关实体：

```
{
    guide_url = "http://m.mafengwo.com", // 酒店攻略详情url
    mdd_areas = [ // 目的地商圈
        { <<目的地区域>>实体
            id: // 区域id, string
            name: // 区域名称, string
            choice_percent: // 选择百分比, float(0-1)
            num_pois: // 区域内的poi数, int
        },
        {
            id: // 区域id, string
            name: // 区域名称, string
            choice_percent: // 选择百分比, float(0-1)
            num_pois: // 区域内的poi数, int
        },
        ...
    ],
    around_pois = [ // 周边pois
        { <<POI>>实体
            id = "poi_around_1",
            name = "故宫"
        },
        ...
    ],
    sort_type = [ // 排序类型(固定的key)
        {
            key = "sort_default",
            name = "默认排序"
        },
        {
            key = "sort_most_comments",
            name = "点评最多"
        },
        {
            key = "sort_expert_suggest",
            name = "达人推荐"
        },
        {
            key = "sort_nearby",
            name = "距离最近"
        },
    ]
    radius_type = [ // 半径范围（当用户当前目的地和$iMddId相同的时候返回）
        {
            key = “1000",
            name = “1000米"
        },
        {
            key = “500",
            name = “500米"
        },
        ...
    ] 
    price_type = [ // 价格范围
        {
            name = “不限制”,
            low = 0,
            high = 0,
        }, 
        {
            name = “1000+”,
            low = 1000,
            high = 0,
        },
        {
            name = “¥200 - ¥251”,
            low = 200,
            high = 251,
        },
        ...
    ]  
    grades_type = [  // 酒店等级
        {
            'key' = 19548 // 将这个数字传给服务器
            'name' = '客栈/青旅'
        }
    ]
}
```