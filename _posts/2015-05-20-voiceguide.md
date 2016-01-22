---
layout: page
title: "翻译官相关"
category: data
date: 2015-03-12 17:11:39
---

# 翻译官推荐
- mapi.mafengwo.cn/voiceguide/recommend/

## 交叉推荐 旅游攻略
- 请求URL：recommends/travelguide/packages/$iPkgId

- 请求方式：GET

- 约束条件：

- 请求参数：

- 返回数据：攻略相关内容

- 相关实体：
    
```
{
    list: [
        {
            img://图片
            url://打开攻略的url scheme
            title://图片下显示的title
            h5://h5页面对应的url
        },
        ...
    ]
}
```