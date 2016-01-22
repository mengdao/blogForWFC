---
layout: page
title: "POI点评"
category: data
date: 2015-03-10 17:14:10
---

# POI点评接口 
- mapi.mafengwo.cn/travelguide/poi/

## 获取指定POI的点评列表
- 请求URL：{poi_id}/comments

- 请求方式：GET

- 约束条件：

- 请求参数： 
    + *start*: 下一页起始位置，使用返回数据的offset，string
    + *length*: 该次取列表数据的长度, 不传默认15条
    
- 返回数据：用户的我的点评列表
- 相关实体：
    + [POI]({% post_url 2015-04-08-entity-poi %}#POI)
    + [POI点评]({% post_url 2015-04-08-entity-poi %}#POI点评)
    + [游记]({% post_url 2015-04-08-entity-note %}#游记)

```
{
    offset = "xxx", 服务器指定结束位置偏移量
    has_more = 0:没有更多，1:还有更多,
    list = [
        { <<POI点评实体>>
            id: // 点评id, string
            comment: // 点评内容, string
            poi:{ <<POI实体>>
                id: // poi id, string
                name: // poi名称, string
                thumbnail: // poi缩略图, string
                type_id: // poi类型, string
            }
            price: // 平均消费价格, float
            rank: // 点评等级(0-5)， int
            sub_ranks:{
                rank_${子评级名称key}: // 点评等级(0-5)， int
                ...
            }
            ctime: // 创建时间(unix时间戳), int
            note: { <<游记实体>>
                id: // 游记id, string
                title: // 游记标题, string
            }
            images: [
                { <<图片实体>>
                    id: // 图片id, string
                    simg: // 小图, string
                    bimg: // 大图, string
                }
            ]
        },
    {
        ...
    },
    ...
]
}
```

## 获取我的指定poi的点评
- 请求URL：{poi_id}/comment

- 请求方式：GET

- 约束条件：必须登录

- 请求参数： 
    
- 返回数据：
    + 有点评：返回用户该iPoiId的点评数据
    + 没点评：返回空结构{}
- 相关实体：
    + [POI]({% post_url 2015-04-08-entity-poi %}#POI)
    + [POI点评]({% post_url 2015-04-08-entity-poi %}#POI点评)
    + [游记]({% post_url 2015-04-08-entity-note %}#游记)

```
{ <<POI点评实体>>
    id: // 点评id, string
    comment: // 点评内容, string
    poi:{ <<POI实体>>
        id: // poi id, string
        name: // poi名称, string
        thumbnail: // poi缩略图, string
        type_id: // poi类型, string
    }
    price: // 平均消费价格, float
    rank: // 点评等级(0-5)， int
    sub_ranks:{
        rank_${子评级名称key}: // 点评等级(0-5)， int
        ...
    }
    ctime: // 创建时间(unix时间戳), int
    note: { <<游记实体>>
        id: // 游记id, string
        title: // 游记标题, string
    }
    images: [
        { <<图片实体>>
            id: // 图片id, string
            simg: // 小图, string
            bimg: // 大图, string
        }
    ]
}
```

## 获取用户点评列表
- 请求URL：comments/users/{user_id}

- 请求方式：GET

- 约束条件：

- 请求参数： 
    + *status*(必传): all, commentted, uncommentted, 全部，已点评，未点评
    + *sub_status*: 不同status不同的子状态值，已点评（all, gold, image, 全部，金牌点评，有图点评）
    + *start*: 下一页起始位置，使用返回数据的offset，string
    + *length*: 该次取列表数据的长度, 不传默认15条
    
- 返回数据：用户的我的点评列表
- 相关实体：
    + [POI]({% post_url 2015-04-08-entity-poi %}#POI)
    + [POI点评]({% post_url 2015-04-08-entity-poi %}#POI点评)
    + [游记]({% post_url 2015-04-08-entity-note %}#游记)

```
{
    offset = "xxx", 服务器指定结束位置偏移量
    has_more = 0:没有更多，1:还有更多,
    list = [
        { <<POI点评实体>>
            id: // 点评id, string
            comment: // 点评内容, string
            poi:{ <<POI实体>>
                id: // poi id, string
                name: // poi名称, string
                thumbnail: // poi缩略图, string
                type_id: // poi类型, string
            }
            price: // 平均消费价格, float
            rank: // 点评等级(0-5)， int
            sub_ranks:{
                rank_${子评级名称key}: // 点评等级(0-5)， int
                ...
            }
            ctime: // 创建时间(unix时间戳), int
            is_gold: // 是否金牌点评, bool(0/1)
            note: { <<游记实体>>
                id: // 游记id, string
                title: // 游记标题, string
            }
            images: [
                { <<图片实体>>
                    id: // 图片id, string
                    simg: // 小图, string
                    bimg: // 大图, string
                }
            ]
        },
    {
        ...
    },
    ...
]
}
```

- 备注：

## 获取某条点评的图片列表
- 请求URL：comments/{comment_id}/images

- 请求方式：GET

- 约束条件：

- 请求参数： 
    
- 返回数据：某条点评的图片列表（不分页，最多20个图片）

```
{
    list = [
                { <<图片实体>>
                    width: // 原图的像素宽度, int
                    height: // 原图的像素宽度, int
                    simg: // 小图, string
                    bimg: // 大图, string
                },
                ...
    ]
}
```

- 备注：


## 发布点评
- 请求URL：{poi_id}/comment

- 请求方式：POST

- 约束条件：必须登录

- 请求参数： 
    + *rank*(必传)  - poi的等级，int，1-5
    + *rank_${子评级key}*(必传)  - poi的该${子评级key}下的等级，int，1-5
    + *content*(必传)  - 点评内容，string
    + *imgs*  - 点评上传图片后的图片存储的URL数组，string，逗号','分割
    + ~~*attr_${属性名称}*  - 该${属性名称}下的值，如下，string~~
        * *输入类型*：值的字符串表示
        * *时间类型*：分钟为单位的值的字符串表示
        * *单选类型*：单选选项名称
        * *多选类型*：多选选项名称的数组，逗号‘,’分割

- 返回数据：点评的结果
    + 成功：返回新增的点评的结构
    + 失败：不返回任何数据
- 相关实体：
    + [POI]({% post_url 2015-04-08-entity-poi %}#POI)
    + [POI点评]({% post_url 2015-04-08-entity-poi %}#POI点评)
    + [游记]({% post_url 2015-04-08-entity-note %}#游记)

```
{
    comment: { <<POI点评实体>>
            id: // 点评id, string
            comment: // 点评内容, string
            poi:{ <<POI实体>>
                id: // poi id, string
                name: // poi名称, string
                thumbnail: // poi缩略图, string
                type_id: // poi类型, string
            }
            price: // 平均消费价格, float
            rank: // 点评等级(0-5)， int
            sub_ranks:{
                rank_${子评级名称key}: // 点评等级(0-5)， int
                ...
            }
            ctime: // 创建时间(unix时间戳), int
            note: { <<游记实体>>
                id: // 游记id, string
                title: // 游记标题, string
            }
            images: [
                { <<图片实体>>
                    id: // 图片id, string
                    simg: // 小图, string
                    bimg: // 大图, string
                }
            ]
        },
}
```

- 备注：
    + ${子评级名称}根据不同poi类型固定写死在客户端
    + ${属性名称}来自于"获取点评属性描述"接口

## 编辑点评
- 请求URL：comments/{comment_id}

- 请求方式：PUT

- 约束条件：必须登录

- 请求参数： 
    + *rank*(必传)  - poi的等级，int，1-5
    + *rank_${子评级key}*(必传)  - poi的该${子评级key}下的等级，int，1-5
    + *content*(必传)  - 点评内容，string
    + *del_img_ids*  - 删除已存在的image的id数组，string，逗号','分割
    + *imgs*  - 新添加的点评上传图片后的图片存储的URL数组，string，逗号','分割
    + ~~*attr_${属性名称}*  - 该${属性名称}下的值，如下，string~~
        * *输入类型*：值的字符串表示
        * *时间类型*：分钟为单位的值的字符串表示
        * *单选类型*：单选选项名称
        * *多选类型*：多选选项名称的数组，逗号‘,’分割

- 返回数据：成功 or 失败
    + 成功：返回该条点评的结构
    + 失败：不返回任何数据
- 相关实体：
    + [POI]({% post_url 2015-04-08-entity-poi %}#POI)
    + [POI点评]({% post_url 2015-04-08-entity-poi %}#POI点评)
    + [游记]({% post_url 2015-04-08-entity-note %}#游记)

```
{
    comment: { <<POI点评实体>>
            id: // 点评id, string
            comment: // 点评内容, string
            poi:{ <<POI实体>>
                id: // poi id, string
                name: // poi名称, string
                thumbnail: // poi缩略图, string
                type_id: // poi类型, string
            }
            price: // 平均消费价格, float
            rank: // 点评等级(0-5)， int
            sub_ranks:{
                rank_${子评级名称key}: // 点评等级(0-5)， int
                ...
            }
            ctime: // 创建时间(unix时间戳), int
            note: { <<游记实体>>
                id: // 游记id, string
                title: // 游记标题, string
            }
            images: [
                { <<图片实体>>
                    id: // 图片id, string
                    simg: // 小图, string
                    bimg: // 大图, string
                }
            ]
        },
}
```

- 备注：
    + ${子评级名称}根据不同poi类型固定写死在客户端
    + ${属性名称}来自于"获取点评扩展信息"接口

## 删除点评
- 请求URL：comments/{comment_id}

- 请求方式：DELETE

- 约束条件：必须登录

- 请求参数： 

- 返回数据：成功 or 失败

## ~~获取POI点评的属性配置~~
- 请求URL：{poi_id}/comments/attributes/config

- 请求方式：GET

- 约束条件：必须登录

- 请求参数： 

- 返回数据：点评扩展信息的列表，后台可控

```
[
    {
        "attr_title":"平均消费",
        "attr_type":1
    },
    {
        "attr_title":"所需时间",
        "attr_type":2
    },
    {
        "attr_title":"游玩方式",
        "attr_type":3,
        "attr_options":["xxx","yyy","zzz"]
    },
    {
        "attr_title":"酒店特色",
        "attr_type":4,
        "attr_options":["xxx","yyy","zzz"]
    },
    ...
]
```

- 备注：
    + ext_type：1=输入类型，2=时间类型，3=单选类型，4=多选类型
    + ext_options：其中3，4两种类型会有该字段，作为选择的候选类型，值为数组，数组元素是string