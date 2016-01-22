---
layout: page
title: "社区"
category: data
date: 2015-05-19 12:45:34
---

# 社区接口
- mapi.mafengwo.cn/travelguide/community/

## 获取打卡状态
- 请求URL：
    + daka

- 请求方式：GET

- 约束条件：必须登录

- 请求参数： 

- 返回数据：

```
{
    user: { <<用户实体>>
        id: // 用户id, string
        name: // 昵称, string
        level: // 用户级别, int
        gender: // 性别, enum(int)
        logo: // 头像缩略图的url, string
        logo_600: // 头像600宽度的url, string
    }
    honey_config: [
        {
            days: // 第几天, int
            honey: // 当前领取的蜂蜜数, int
        },
        ...
    ]
    experience_percent: // 经验到满经验的百分比, float
    counter_days: // 打卡累计天数, int
    counter_honey_days: // 打卡绑定蜂蜜功能上线后打卡累计天数, int
    result: // 今天是否打卡, bool
}
```

## 打卡
- 请求URL：
    + daka

- 请求方式：POST

- 约束条件：必须登录

- 请求参数： 

- 返回数据：

```
{
    user: { <<用户实体>>
        id: // 用户id, string
        name: // 昵称, string
        level: // 用户级别, int
        gender: // 性别, enum(int)
        logo: // 头像缩略图的url, string
        logo_600: // 头像600宽度的url, string
    }
    honey_config: [
        {
            days: // 第几天, int
            honey: // 当前领取的蜂蜜数, int
        },
        ...
    ]
    honey_added: // 当次打卡所获取的蜂蜜数量, int
    honey_added_msg: // 当次打卡结果的文字消息, string
    experience_percent: // 经验到满经验的百分比, float
    experience_added: // 当次打卡所获取的经验数量, int
    counter_days: // 当次打卡累计天数, int
    counter_honey_days: // 打卡绑定蜂蜜功能上线后当次打卡累计天数, int
    result: // 是否打卡, bool
}
```

## 运营活动
- 请求URL：
    + activities/pages/user_poi_comments

- 请求方式：GET

- 约束条件：

- 请求参数： 

- 返回数据：

```
{
    list: [
        {
            title: // 活动标题, string
            jump_url: // 活动跳转h5的url或者sharejump, string
        }
        , ...
    ]
}
```