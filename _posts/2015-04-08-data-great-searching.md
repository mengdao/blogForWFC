---
layout: page
title: "大搜索"
category: data
date: 2015-04-08 10:57:14
---

# 大搜索接口
- mapi.mafengwo.cn/travelguide/sdata/

## 统一搜索 

- 请求URL：
    + data
    + data/mdds/{mdd_id}

- 请求方式：GET

- 约束条件：

- 请求参数： 
    + *keyword*(必传): 关键词, string
    + *c_lat* : 当前位置的纬度，6位小数, float
    + *c_lng* : 当前位置的经度，6位小数, float
    
- 返回数据：搜索结果列表
- 相关实体：
    + [目的地]({% post_url 2015-04-08-entity-mdd %}#目的地)
    + [POI]({% post_url 2015-04-08-entity-poi %}#poi)
    + [酒店:POI]({% post_url 2015-04-08-entity-poi %}#酒店:poi)
    + [结构化攻略]({% post_url 2015-04-08-entity-book %}#结构化攻略)
    + [问题]({% post_url 2015-04-08-entity-qna %}#问题)
    + [游记]({% post_url 2015-04-08-entity-note %}#游记)
    + [用户]({% post_url 2015-04-08-entity-user %}#用户)

```
{
    participles = [ // 在关键词搜索中，返回搜索关键词的分词结果，例：我想吃馒头
        "我", "想", "吃", "馒头", "我想", "吃馒头", "想吃", "我想吃", "我想吃馒头", ... 
    ],
    list = [
                {   
                    title: // 标题, string
                    type: // 搜索结果类型, string(mdds,pois,hotels,books,questions,notes,users等)

                    // 根据type会返回不同字段的数组，其中各自的元素也不同，
                    // 字段包括mdds,pois,hotels,books,questions,notes,users,结构如下:
                    mdds: [
                        { <<目的地>>
                            id: // 目的地id, string
                            name: // 目的地名称, string
                            lat: // 纬度，6位小数, double
                            lng: // 经度，6位小数, double
                            parent: { 父级<<目的地>>
                                id: // 目的地id, string
                                name: // 目的地名称, string
                                }
                            thumbnail: // 缩略图url, string
                            num_have_been: // 多少蜂蜂去过的数, int
                            num_want_go: // 多少蜂蜂想去的数, int
                            jump_url: // 跳转的sharejump或url链接, string
                        }, 
                        ...]
                    | // 这里是或！！！
                    pois: [
                        { <<POI>>
                            id: // POI id, string
                            name: // 名称, string
                            foreign_name: // 外语名称, string
                            rank: // 等级 0-5, int
                            type_id: // 类型, enum(int)
                            thumbnail: // 缩略图url, string
                            num_comment: // 点评数量, int
                            num_travelnote: // 相关游记数量, int
                            mdd: { 归属<<目的地>>
                                id: // 目的地id, string
                                name: // 目的地名称, string
                                },
                            jump_url: // 跳转的sharejump或url链接, string 
                            distance: // 当前位置距该POI的距离描述(单位：米), int
                        }, 
                        ...]
                    | // 这里是或！！！
                    hotels: [
                        { <<酒店:POI>>
                            id: // 酒店POI id, string
                            name: // 名称, string
                            foreign_name: // 外语名称, string
                            rank: // 等级 0-5, int
                            price: // 消费价格, float
                            price_type: // 消费价格单位(货币符号), string
                            type_id: // 类型, enum(int)
                            thumbnail: // 缩略图url, string
                            num_comment: // 点评数量, int
                            num_travelnote: // 相关游记数量, int
                            mdd: { 归属<<目的地>>
                                id: // 目的地id, string
                                name: // 目的地名称, string
                                },
                            jump_url: // 跳转的sharejump或url链接, string
                            distance: // 当前位置距该POI的距离描述(单位：米)，小于0为无效距离, int
                        }, 
                        ...]
                    | // 这里是或！！！
                    books: [
                        { <<结构化攻略>>
                            id: // 攻略id, string
                            title: // 标题, string
                            subtitle: // 子标题, string
                            mddid: // 目的地id, string
                            mddname: // 目的地名称, string
                            mdd: { 所属<<目的地>>
                                id: // 目的地id, string
                                name: // 目的地名称, string
                                },
                            cover: // 封面缩略图url, string
                            utime: // 更新时间(unix时间戳，秒), int
                            file: // 攻略下来url, string
                            size: // 攻略大小(单位:字节), long long
                            ver: // 攻略版本号, string
                            catalog_online: // 在线攻略结构, JSON object
                            jump_url: // 跳转的sharejump或url链接, string
                        }, 
                        ...]
                    | // 这里是或！！！
                    questions: [
                        { <<问题>>
                            id: // 问题id, string
                            title: // 标题, string
                            content: // 内容, string
                            ctime: // 创建时间(unix时间戳，秒), int
                            mdd: { 所属<<目的地>>
                                id: // 目的地id, string
                                name: // 目的地名称, string
                                },
                            num_answer: // 回答数量, int
                            jump_url: // 跳转的sharejump或url链接, string
                        }, 
                        ...]
                    | // 这里是或！！！
                    notes: [
                        { <<游记>>
                            id: // 游记id, string
                            ctime: // 创建时间(unix时间戳，秒), int
                            title: // 标题, string
                            digest: // 摘要, string
                            thumbnail: // 缩略图url, string
                            num_visit: // 浏览数量, int
                            mdds: [ 所属<<目的地>>列表, array[entity]
                                {
                                id: // 目的地id, string
                                name: // 目的地名称, string
                                },...
                            ]
                            jump_url: // 跳转的sharejump或url链接, string
                        }, 
                        ...]
                    | // 这里是或！！！
                    users: [
                        { <<用户>>
                            id: // 用户id, string    
                            name: // 昵称, string
                            level: // 用户级别, int
                            gender: // 性别, enum(int)
                            logo: // 头像缩略图的url, string
                            intro: // 签名, string
                            num_fans: // 粉丝数, int
                            num_follows: // 关注数, int
                            footprint_info: { <<用户足迹信息>>
                                state_num: // 国家数, int
                                city_num: // 城市数, int
                                foot_num: // 足迹数, int
                            }
                            jump_url: // 跳转的sharejump或url链接, string
                        }, 
                        ...]
                    ,
                    has_more: // 是否显示查看更多xxx, bool
                    more_text: // 查看更多的文字描述, string
                },
                ...
    ]
}
```

### 接口详细解释：
    - 参数使用：
        + $iMddid 指定目的地查询时用
        + keyword 关键词搜索时用
    - 返回结构：
        + 为适配搜索的扩展内容的支持，请求接口的代码要统一过滤当前支持的type种类的白名单
        + 不同的type类型，返回的字段是有区别的，会根据type类型做设置

## 分类搜索 

- 请求URL：
    + data/{entity_type}
    + data/{entity_type}/mdds/$iMddId
    + 注：*entity_type*为【[统一搜索](#统一搜索)】支持的类型, string

- 请求方式：GET

- 约束条件：

- 请求参数： 
    + *keyword*(必传): 关键词, string
    + *start*: 下一页起始位置，使用返回数据的offset，string
    + *length*: 该次取列表数据的长度, 不传默认15条
    + *c_lat* : 当前位置的纬度，6位小数, float
    + *c_lng* : 当前位置的经度，6位小数, float
    
- 返回数据：根据type类型返回相关搜索结果列表，支持翻页

```
{
    offset = "xxx", 服务器指定结束位置偏移量
    has_more = 0:没有更多，1:还有更多,
    list = [
        { 根据类型返回【统一搜索】中指定类型返回的数据格式（完全一样）
        },
        ...
    ]
}
```

## 搜索推荐词接口(支持指定类型)
- 请求URL：
    + suggestions
    + suggestions/mdds/{mdd_id} *指定目的地*
    + suggestions/{entity_type} *指定类型*
    + suggestions/{entity_type}/mdds/{mdd_id} *指定类型&目的地*
    + 注：*entity_type*为【[统一搜索](#统一搜索)】支持的类型, string

- 请求方式：GET

- 约束条件：

- 请求参数： 
    + *keyword*(必传): 关键词, string
    + *c_lat* : 当前位置的纬度，6位小数, float
    + *c_lng* : 当前位置的经度，6位小数, float

- 返回数据：根据关键词的推荐词列表
- 相关实体：无
    
```
{
    participles = [ // 在关键词搜索中，返回搜索关键词的分词结果，例：我想吃馒头
        "我", "想", "吃", "馒头", "我想", "吃馒头", "想吃", "我想吃", "我想吃馒头", ... 
    ],
    list = [ 
        {
            name: // 推荐关键词名称, string
            subname: // 关键词相关子标题名称, string
            icon: // 类型图标url, string
            url: // 跳转的sharejump或url链接, string
            data:{
                poi:{ // <<POI实体>> 如果该类型是pois，则会有此字段
                    lat: // 纬度，6位小数, double
                    lng: // 经度，6位小数, double
                }
            }
        },
        ...
    ], 
}
```


## 周边搜索 

- 请求URL：
    + data/lat/{lat}/lng/{lng}/radius/{radius}

- 请求方式：GET

- 约束条件：

- 请求参数： 
    + *redirect_to_mddid* : 如果传递，则重定向到指定目的地的id(忽略当前坐标，以目的地为搜索范围), string
    + *type* : 分类type(pois), 多选以','分割, string 
    + *sub_type* : 分类中的子类型，(':'分割type块, ','分割subtype多选), string
    + *c_lat* : 当前位置的纬度，6位小数, float
    + *c_lng* : 当前位置的经度，6位小数, float
    
- 返回数据：搜索结果列表
    + c_mdd: 当前所在目的地（如果有传当前位置）
    + s_mdd: 搜索坐标所在目的地
    + r_mdd: 有此返回字段你表示该数据已被重定向到指定目的地(如果有传redirect_to_mddid)
- 相关实体：
    + [目的地]({% post_url 2015-04-08-entity-mdd %}#目的地)
    + [POI]({% post_url 2015-04-08-entity-poi %}#poi)
    + [用户]({% post_url 2015-04-08-entity-user %}#用户)

```
{
    r_mdd = { <<目的地>>, 重定向目的地，如果有传的话
        id: // 目的地id, string
        name: // 目的地名称, string
        lat: // 纬度，6位小数, double
        lng: // 经度，6位小数, double
    },
    list = [
                {   
                    type: // 搜索结果类型, string(pois等)

                    // 根据type会返回不同字段的数组，其中各自的元素也不同，
                    // 字段包括pois,结构如下:
                    pois: [
                        { <<POI>>
                            id: // POI id, string
                            name: // 名称, string
                            foreign_name: // 外语名称, string
                            rank: // 等级 0-5, int
                            type_id: // 类型, enum(int)
                            price: // 消费价格, float
                            price_type: // 消费价格单位, string
                            thumbnail: // 缩略图url, string
                            num_comment: // 点评数量, int
                            num_travelnote: // 相关游记数量, int
                            num_footprint: // 总计添加过足迹的人的数量，int
                            honors:[ // 荣耀列表 
                                { <POI荣耀结构>
                                    title: // 荣耀名称
                                    s_icon_url: // 荣耀小图标url
                                },
                                ...
                            ]
                            jump_url: // 跳转的sharejump或url链接, string
                            recent_users = [ // 最近来过的用户列表
                                { // <<用户实体>>
                                    id: // 用户id, string
                                    name: // 用户名, string
                                    logo: // 头像缩略图的url, string
                                    jump_url: // 页面的url, string
                                },
                                ...
                            ],
                            distance: // 当前位置距该POI的距离描述(单位：米), int
                            is_fav: // 是否收藏, bool
                        }, 
                        ...]
                },
                ...
    ]
}
```

### 接口详细解释：
    - 参数使用：
        + $lat, $lng, $radius 中心点加半径确定范围搜索时用，优先坐标半径
    - 返回结构：
        + 为适配搜索的扩展内容的支持，请求接口的代码要统一过滤当前支持的type种类的白名单
        + 不同的type类型，返回的字段是有区别的，会根据type类型做设置
