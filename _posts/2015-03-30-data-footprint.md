---
layout: page
title: "足迹"
category: data
date: 2015-03-30 11:21:05
---

# 足迹接口 
- mapi.mafengwo.cn/travelguide/footprint/

## 获取用户足迹的目的地时间线
- 请求URL：mdds/timeline/users/{user_id}

- 请求方式：GET

- 约束条件：

- 请求参数： 
    + *start*: 下一页起始位置，使用返回数据的offset, string
    + *length*: 该次取列表数据的长度，不传默认15条, int
    + *sort_type*: 排序方式（sort_by_time(默认), sort_by_country）, string
        - 注：不同的排序方式根据展示需要可能需要不同的重组方式
- 返回数据：
- 相关实体：
    + [POI点评]({% post_url 2015-04-08-entity-poi %}#POI点评)
    + [目的地]({% post_url 2015-04-08-entity-mdd %}#目的地)

```
{
    ex = {
        num_uncomment_pois: // 未点评的足迹数, int
    }
    offset = "xxx", 服务器指定结束位置偏移量
    has_more = 0:没有更多，1:还有更多,
    list = [
        {
            mdd: { <<目的地>>
                id: // 目的地id, string
                name: // 目的地名称, string
                thumbnail: // 缩略图, string
                lat: // 纬度，6位小数, double
                lng: // 经度，6位小数, double
                is_country: // 是否为国家, bool
                parent: { <<目的地>>
                    id: // 目的地id, string
                    name: // 目的地名称, string
                    thumbnail: // 缩略图, string
                    lat: // 纬度，6位小数, double
                    lng: // 经度，6位小数, double
                    is_country: // 是否为国家, bool
                    parent: { <<目的地>>
                        id: // 目的地id, string
                        name: // 目的地名称, string
                        thumbnail: // 缩略图, string
                        lat: // 纬度，6位小数, double
                        lng: // 经度，6位小数, double
                        is_country: // 是否为国家, bool
                    }
                }
            }
            year: // 足迹添加年, int
            month: // 足迹添加月份, int
            day: // 足迹添加日, int
            num_footprint: // 该目的地的足迹数, int
            num_poi_comment: // 该目的地的足迹点评数, int
            num_gold_poi_comment: // 该目的地的足迹金牌点评数, int
            is_new: // 是否为当前用户新添加的（未阅读/未进入过该目的地足迹页）, bool
        },
        ...
    ]
}
```


## 获取某用户某目的地下的足迹列表
- 请求URL：footprints/users/{user_id}/mdds/{mdd_id}

- 请求方式：GET

- 约束条件：

- 请求参数： 
    + *start*: 下一页起始位置，使用返回数据的offset，string
    + *length*: 该次取列表数据的长度, 不传默认15条
    
- 返回数据：
    + 带comment字段，表示有点评；否则，没有做点评
- 相关实体：
    + [足迹]({% post_url 2015-04-14-entity-footprint %}#足迹)
    + [POI]({% post_url 2015-04-08-entity-poi %}#POI)
    + [POI点评]({% post_url 2015-04-08-entity-poi %}#POI点评)
    + [目的地]({% post_url 2015-04-08-entity-mdd %}#目的地)

```
{
    offset = "xxx", 服务器指定结束位置偏移量
    has_more = 0:没有更多，1:还有更多,
    ex = { // 接口扩展信息
        num_comments, // 点评数, int
        num_footprints, // 足迹数, int
        num_gold_comments // 金牌点评数, int
    },
    mdd = { <<目的地实体>>
        id: // 目的地id, string
        name: // 目的地名称, string
    }，
    list = [
        { <<足迹实体>>
            "id": // 足迹id, string
            poi:{  <<POI实体>>
                id: // poi id, string
                name: // poi名称, string
                thumbnail: // poi缩略图, string
                type_id: // poi类型, int
            }
            comment: { <<POI点评实体>>
                id: // 点评id, string
                comment: // 点评内容, string
                rank: // 点评等级(0-5), int
                sub_ranks:{
                   rank_${子评级名称key}: // 点评等级(0-5)， int
                    ...
                }
                images: [
                    {
                        id: // 图片id, string
                        simg: // 小图, string
                        bimg: // 大图, string
                    },
                    ...
                ]
                is_gold: // 是否金牌点评, bool(0/1)
                owner: { <<用户实体>>
                   id: // 用户id
                    name: // 用户昵称
                    logo: // 用户头像
                }
            },
        },
        {
            ...
        },
        ...
    ]
}
```

- 备注：

## 获取我的指定POI足迹
- 请求URL：
    + pois/{poi_id}/footprint // 用户在目的地的足迹是唯一的

- 请求方式：GET

- 约束条件：必须登录

- 请求参数： 

- 返回数据：
    + 有点评：返回用户该iPoiId的足迹数据
    + 没点评：返回空结构{}
- 相关实体：
    + [足迹]({% post_url 2015-04-14-entity-footprint %}#足迹)
    + [POI]({% post_url 2015-04-08-entity-poi %}#POI)
    + [目的地]({% post_url 2015-04-08-entity-mdd %}#目的地)

```
{ <<足迹实体>>
    "id": 6724830, // 足迹id, string
    poi:{  <<POI实体>>
        id: // poi id, string
        name: // poi名称, string
        thumbnail: // poi缩略图, string
        type_id: 5, // poi类型, int
        mdd: { <<目的地实体>>
            id: // 目的地id, string
            name: // 目的地名称, string
        }
    }
}
```


## 添加我的POI足迹(单条，可指定mdd)
- 请求URL：pois/{poi_id}/footprint

- 请求方式：POST

- 约束条件：必须登录

- 请求参数： 
    + *rank*(可选): 评星，1-5，不传默认3星
    + *mddid*(选传): 意味着将这些poi都添加到该mdd下，如果不传，则表示添加poi到该poi最近的mdd下
- 返回数据：
    + footprint: 足迹实体结构
- 相关实体：
    + [足迹]({% post_url 2015-04-14-entity-footprint %}#足迹)
    + [POI]({% post_url 2015-04-08-entity-poi %}#POI)
    + [目的地]({% post_url 2015-04-08-entity-mdd %}#目的地)

```
{
    footprint = { <<足迹实体>>
            "id": 6724830, // 足迹id, string
            poi:{  <<POI实体>>
                id: // poi id, string
                name: // poi名称, string
                thumbnail: // poi缩略图, string
                type_id: 5, // poi类型, int
                mdd: { <<目的地实体>>
                    id: // 目的地id, string
                    name: // 目的地名称, string
                }
            }
        }
}
```

## 添加我的POI足迹(多条，可指定mdd)
- 请求URL：pois/footprints

- 请求方式：POST

- 约束条件：必须登录

- 请求参数： 
    + *poiids*(必传): 逗号','分隔的poiid, string
    + *mddid*(选传): 意味着将这些poi都添加到该mdd下，如果不传，则表示添加poi到该poi最近的mdd下

- 返回数据：
    + list: 添加的足迹实体列表
- 相关实体：
    + [足迹]({% post_url 2015-04-14-entity-footprint %}#足迹)
    + [POI]({% post_url 2015-04-08-entity-poi %}#POI)
    + [目的地]({% post_url 2015-04-08-entity-mdd %}#目的地)

```
{
    list = { <<足迹实体>>
            "id": 6724830, // 足迹id, string
            poi:{  <<POI实体>>
                id: // poi id, string
                name: // poi名称, string
                thumbnail: // poi缩略图, string
                type_id: 5, // poi类型, int
                mdd: { <<目的地实体>>
                    id: // 目的地id, string
                    name: // 目的地名称, string
                }
            }
        }
}
```


## 删除我的POI足迹(单条)
- 请求URL：
    + pois/{poi_id}/footprint // 用户在POI的足迹是唯一的

- 请求方式：DELETE

- 约束条件：必须登录

- 请求参数： 

- 返回数据：成功 or 失败
- 相关实体：


## 删除我的POI足迹(多条)
- 请求URL：
    + pois/footprints // 用户在POI的足迹是唯一的

- 请求方式：DELETE

- 约束条件：必须登录

- 请求参数： 
    + *poiids*(必传): 逗号','分隔的poiid, string 

- 返回数据：成功 or 失败
- 相关实体：


## 添加我的目的地足迹(单条)
- 请求URL：mdds/{mdd_id}/footprint

- 请求方式：POST

- 约束条件：必须登录

- 请求参数： 

- 返回数据：成功 or 失败
- 相关实体：


## 添加我的目的地足迹(多条)
- 请求URL：mdds/footprints

- 请求方式：POST

- 约束条件：必须登录

- 请求参数： 
    + *mddids*(必传): 逗号','分隔的目的地id, string

- 返回数据：成功 or 失败
- 相关实体：


## 删除我的目的地足迹(单条)
- 请求URL：
    + mdds/{mdd_id}/footprint // 用户在目的地的足迹是唯一的

- 请求方式：DELETE

- 约束条件：必须登录

- 请求参数： 

- 返回数据：成功 or 失败
- 相关实体：


## 删除我的目的地足迹(多条)
- 请求URL：
    + mdds/footprints // 用户在POI的足迹是唯一的

- 请求方式：DELETE

- 约束条件：必须登录

- 请求参数： 
    + *mddids*(必传): 逗号','分隔的目的地id, string 

- 返回数据：成功 or 失败
- 相关实体：

## 获取足迹中的中国省级目的地列表
- 请求URL：metadata/mdds/china_provinces

- 请求方式：GET

- 约束条件：

- 请求参数： 
    
- 返回数据：
- 相关实体：
    + [目的地]({% post_url 2015-04-08-entity-mdd %}#目的地)

```
{
    list = [
        { <<目的地>>
            id: // 目的地id, string
            name: // 目的地名称, string
            pinyin: // 目的地名称的拼音, string
        },
        ...
    ]
}
```

## 获取足迹中的中国省级目的地列表
- 请求URL：metadata/mdds/china_provinces

- 请求方式：GET

- 约束条件：

- 请求参数： 
    
- 返回数据：
- 相关实体：
    + [目的地]({% post_url 2015-04-08-entity-mdd %}#目的地)

```
{
    list = [
        { <<目的地>>
            id: // 目的地id, string
            name: // 目的地名称, string
            pinyin: // 目的地名称的拼音, string
        },
        ...
    ]
}
```

## 获取足迹中的外国国家目的地列表
- 请求URL：metadata/mdds/foreign_countries

- 请求方式：GET

- 约束条件：

- 请求参数： 
    
- 返回数据：
- 相关实体：
    + [目的地]({% post_url 2015-04-08-entity-mdd %}#目的地)

```
{
    list = [
        { <<目的地>>
            id: // 目的地id, string
            name: // 目的地名称, string
            foreign_name: // 外语名称, string
            pinyin: // 目的地名称的拼音, string
            hot: // 热门度（0代表不是热门，非0都是热门并且可以按照热门度排序）, int
        },
        ...
    ]
}
```

## 获取足迹城市目的地列表
- 请求URL：metadata/mdds/cities

- 请求方式：GET

- 约束条件：

- 请求参数： 
    + *keyword*(必传，暂时不支持不传关键词进行获取): 城市目的地关键词, string
    + *start*: 下一页起始位置，使用返回数据的offset, string
    + *length*: 该次取列表数据的长度, 不传默认15条, int
    
- 返回数据：
- 相关实体：
    + [目的地]({% post_url 2015-04-08-entity-mdd %}#目的地)

```
{
    offset = "xxx", 服务器指定结束位置偏移量
    has_more = 0:没有更多，1:还有更多,
    list = [
        { <<目的地>>
            id: // 目的地id, string
            name: // 目的地名称, string
            foreign_name: // 外语名称, string
            thumbnail: // 缩略图url, string
            num_have_been: // 多少蜂蜂去过的数量, int
            have_been: // 当前用户是否去过, bool
        },
        ...
    ]
}
```

## 获取足迹中的目的地子城市目的地列表
- 请求URL：metadata/mdds/{mdd_id}/cities

- 请求方式：GET

- 约束条件：

- 请求参数： 
    
- 返回数据：
    + $iMddId 必须是中国的省级目的地，或国外的国家目的地，否则返回空
- 相关实体：
    + [目的地]({% post_url 2015-04-08-entity-mdd %}#目的地)

```
{
    list = [
        { <<目的地>>
            id: // 目的地id, string
            name: // 目的地名称, string
            foreign_name: // 外语名称, string
            thumbnail: // 缩略图url, string
            num_have_been: // 多少蜂蜂去过的数量, int
            have_been: // 当前用户是否去过, bool
        },
        ...
    ]
}
```

## 获取足迹中的城市目的地的POI列表
- 请求URL：metadata/mdds/{mdd_id}/pois

- 请求方式：GET

- 约束条件：

- 请求参数： 
    + *type*: poi类型(不传，则默认全部), enum(int)
    + *keyword*(选传): 搜索关键词，作为删选条件, string
    + *start*: 下一页起始位置，使用返回数据的offset, string
    + *length*: 该次取列表数据的长度, 不传默认15条, int

- 返回数据：
    + $iMddId 必须是城市目的地，否则返回空
- 相关实体：
    + [POI]({% post_url 2015-04-08-entity-poi %}#POI)

```
{
    offset = "xxx", 服务器指定结束位置偏移量
    has_more = 0:没有更多，1:还有更多,
    list = [
        {  <<POI实体>>
            id: // poi id, string
            name: // poi名称, string
            foreign_name: // poi外语名称, string
            type_id: // poi类型, int
            thumbnail: // 缩略图url, string
            num_footprint: // 多少蜂蜂去过的数量, int
            have_been: // 当前用户是否去过, bool
        },
        ...
    ]
}
```

