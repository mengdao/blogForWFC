---
layout: page
title: "广告"
category: data
date: 2015-06-03 16:41:03
---

# 广告接口
- mapi.mafengwo.cn/travelguide/ad/

## 获取不同位置的静态广告内容
- 请求URL：
    + ads/statics/home_banner 
    + ads/statics/home_bottom 
    + ads/statics/mdd_banner 

- 请求方式：GET

- 约束条件：

- 请求参数： 
    + 该ads/statics/mdd_banner
        - *mddid*: // 目的地id, string
    + 其他两个接口需要传参数

- 返回数据：

```
{
    list: [
        {
            id: // 静态广告id, string
            title: // 静态广告标题, string
            img_url: // 广告图的url，不同位置的广告图片的大小应该在后台做区别, string
            jump_url: // 点击该广告图，跳转h5的url或者sharejump, string
        }
        , ...
    ]
}
```


## 获取浮动广告配置
- 请求URL：
    + ads/floatings/config

- 请求方式：GET

- 约束条件：

- 请求参数： 
    + *c_lat* : 当前位置的纬度，6位小数, float
    + *c_lng* : 当前位置的经度，6位小数, float

- 返回数据：

```
{
    list: [
        {
            id: // 浮动广告id, string
            title: // 浮动广告名称, string
            content: // 浮动广告描述, string

            style: {
                name: // 浮动广告展现类型名称（rb_corner, fullscreen, rb_corner_to_fullscreen）, string
                rb_img: { // 浮动广告小<<图片实体>>
                    width: // 图片原始像素高度, int
                    height: // 图片原始像素高度, int
                    oimg: // 图片url, string
                },
                rb_img_is_apng: // 是否为apng, bool
                rb_icon_apng_play_interval: // 每一遍播放APNG的间隔（秒）, float
                rb_img_rm: // 小图标右边距, int
                rb_img_bm: // 小图标下边距, int
                fs_img: { // 浮动广告大<<图片实体>>
                    width: // 图片原始像素高度, int
                    height: // 图片原始像素高度, int
                    oimg: // 图片url, string
                },
            }

            page_name: // 浮动广告展现的页面名称, string
            page_related_data: { // 浮动广告位所在页面的相关基础数据, dictionary
                ...
            }
            
            display_once: // 只显示一次, bool
            click_to_hide_forever: // 点击后不再显示, bool

            need_login: // 是否需要登录才能触发跳转行为, bool
            need_login_title: // 是否需要登录的提示的文字标题, string
            
            jump_condition: // 跳转条件(no_condition, need_request), string
            jump_url: // 浮动广告跳转url或sharejump, string，当jump_condition==need_request时没有此字段

            start_time: // 开始时间的UNIX时间戳，单位秒, int
            end_time: // 结束时间的UNIX时间戳，单位秒, int

            priority: // 优先级, int
        }
        , ...
    ]
}
```


## 浮动广告响应接口
- 请求URL：
    + ads/floatings/{float_ad_id}/response

- 请求方式：POST

- 约束条件：

- 请求参数： 
    + *c_lat* : 当前位置的纬度，6位小数, float
    + *c_lng* : 当前位置的经度，6位小数, float

- 返回数据：

```
{
    adid: // 浮动广告id, string
    result: // 允许跳转, bool
    message: // 请求结果的响应消息（如果为空，则不显示响应消息）, string
    jump_url: // 浮动广告跳转url或sharejump（不允许则不返回此字段）, string
}
```

