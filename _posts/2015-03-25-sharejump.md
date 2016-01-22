---
layout: page
title: "ShareJump及scheme规范"
category: ios
date: 2015-03-25 18:55:47
---

# Scheme方式，应用间跳转
```
sharejump_url = http://m.mafengwo.cn/nb/public/sharejump.php?type=1&id=29
encoded_sharejump_url = urlencode($sharejump_url)

travelguide://jump?url={$encoded_sharejump_url}
```

# 应用内ShareJump跳转

### [0] 跳转url

| 参数名称 | 是否必选| 参数说明 |
|-----|----------|---------|
|url	|required|	网页连接|
|title	|optional|	标题|
|source	|optional|来源|
|loading|optional|第一个url是否使用loading条|

### [1] 攻略详情

| 设备|地址|
|---|---|
| App|http://m.mafengwo.cn/nb/public/sharejump.php?type=1&id=29|
| web|http://www.mafengwo.cn/gonglve/mdd-{$mdd_id}.html|
| H5 |http://m.mafengwo.cn/baike/{$mdd_id}/|


----

| 参数名称 | 是否必选| 参数说明 |
|-----|----------|---------|
|id		|required|攻略id|
|title	|optional|	攻略名称|

### [2] 专题详情(支持PUSH)

| 设备|地址|
|---|---|
| App|http://m.mafengwo.cn/nb/public/sharejump.php?type=2&id={$id}|
| web|http://www.mafengwo.cn/mobile/public/common_html.php?id={$id}|
| H5 |http://www.mafengwo.cn/mobile/public/common_html.php?id={$id}|

----

| 参数名称 | 是否必选| 参数说明 |
|-----|----------|---------|
|id		|required|专题id|
|title	|optional|	专题名称|
|url	|optional|专题url|

### [3] POI详情页

| 设备|地址|
|---|---|
| App|http://m.mafengwo.cn/nb/public/sharejump.php?type=3&id={$id}|
| web|http://www.mafengwo.cn/poi/{$id}.html|
| H5 |http://m.mafengwo.cn/poi/{$id}.html|

----

| 参数名称 | 是否必选| 参数说明 |
|-----|----------|---------|
|id		|required|poi id|
|title  |optional|标题|


### [4] ~~攻略列表（攻略分组id获取）(已废弃）~~

### [5] 攻略列表（按mddid）获取

| 设备|地址|
|---|---|
| App|http://m.mafengwo.cn/nb/public/sharejump.php?type=5&id={$id}|
| web|http://www.mafengwo.cn/travel-scenic-spot/mafengwo/{$id}.html|
| H5 |http://m.mafengwo.cn/mdd/{$id}|

----

| 参数 | 是否必选| 参数说明 |
|-----|----------|---------|
|id		|required|目的地id|
|title	|optional|	目的地名称|

### [6] 消息中心(支持PUSH)

|参数|是否可选|参数说明|
|----   |-----   |-----   |
|msg_type|optional|消息类型|


### [7] 游记详情(支持PUSH)

| 设备|地址|
|---|---|
| App|http://m.mafengwo.cn/nb/public/sharejump.php?type=7&id={$id}|
| web|http://www.mafengwo.cn/i/{$id}.html|
| H5 |http://m.mafengwo.cn/i/{$id}.html|
|with_push|required|1支持 push,0或空不支持|


----

| 参数 | 是否必选| 参数说明 |
|-----|----------|---------|
|id	|required|游记id|

### [8] ~~poi榜单(已废弃）~~


### [9] 特价(支持PUSH)

| 设备|地址|
|---|---|
| App|http://m.mafengwo.cn/nb/public/sharejump.php?type=9&id={$id}|
| web|http://www.mafengwo.cn/sales/{$id}.html|
| H5 |http://m.mafengwo.cn/sales/info.php?id={$id}|

----

| 参数 | 是否必选| 参数说明 |
|-----|----------|---------|
|id	|required|特价id|

### [10] 目的地详情

| 设备|地址|
|---|---|
| App|http://m.mafengwo.cn/nb/public/sharejump.php?type=10&id={$id}|
| web|http://www.mafengwo.cn/travel-scenic-spot/mafengwo/{$id}.html|
| H5 |http://m.mafengwo.cn/mdd/{$id}|

----

| 参数 | 是否必选| 参数说明 |
|-----|----------|---------|
|id	|required|目的地id|

### [11] 目的地游记列表

| 设备|地址|
|---|---|
| App|http://m.mafengwo.cn/nb/public/sharejump.php?type=11&mddid={$mddid}|
| web|http://www.mafengwo.cn/yj/{$mddid}/|
| H5 |http://m.mafengwo.cn/mdd/{$mddid}|

----

| 参数 | 是否必选| 参数说明 |
|-----|----------|---------|
|mddid	|required|目的地id|
|mddname	|optional|目的地名称|
|who_type	|optional|人物（请参考旅游攻略接口文档）|
|travel_type	|optional|形式（请参考旅游攻略接口文档）|
|month_min	|optional|月份起始（整数）|
|month_max	|optional|月份结束（整数）|
|price_min	|optional|价格起始（整数）|
|price_max	|optional|价格结束（整数）|
|sort_type	|optional|排序类型（请参考旅游攻略接口文档）|

### [12] 目的地POI列表

| 设备|地址|
|---|---|
| App|http://m.mafengwo.cn/nb/public/sharejump.php?type=12&mddid={$mddid}&type_id=2|
| web|http://www.mafengwo.cn/hotel/{$mddid}/|
| H5 |http://m.mafengwo.cn/hotel/{$mddid}/|

----

| 参数 | 是否必选| 参数说明 |
|-----|----------|---------|
|mddid	|required|目的地id|
|type_id	|required|poi类型|
|mddname	|optional|目的地名称|
|area_id	|optional|商圈id|
|near	|optional|是否优先取附近（1：是，0：否）|
|keyword	|optional|关键词|
|price_min	|optional|价格起始（整数）|
|price_max	|optional|价格结束（整数）|
|lat	|optional|纬度|
|lng	|optional|经度|
|lat_delta	|optional|纬度跨度|
|lng_delta	|optional|经度跨度|
|sort_type	|optional|排序类型（请参考旅游攻略接口文档）|
|checkin	|optional|入住时间（例如：2014-05-06）|
|checkout	|optional|离店时间（例如：2014-05-10）|
|has_booking_rooms|optional|如果为1 而且是酒店 则只显示有房的酒店|

### [13] 推荐分组详情(支持PUSH)

| 设备|地址|
|---|---|
| App|http://m.mafengwo.cn/nb/public/sharejump.php?type=13&id={$id}|

----

| 参数 | 是否必选| 参数说明 |
|-----|----------|---------|
|id	|required|分组id|
|title		|optional|分组标题|


### [14] 酒店预订(无参数）

### [15] 搜索结果页

| 参数 | 是否必选| 参数说明 |
|-----|----------|---------|
|keyword	|required|关键词|
|tab		|optional|标签：0目的地、1离线攻略、2游记、3问答；不传则默认为0目的地|

### [16] 特价列表

| 设备|地址|
|---|---|
| App|http://m.mafengwo.cn/nb/public/sharejump.php?type=16 <br>http://m.mafengwo.cn/nb/public/sharejump.php?type=16&mddid=10065|
| web|http://www.mafengwo.cn/sales/|
| H5 |http://m.mafengwo.cn/sales/|

----

| 参数 | 是否必选| 参数说明 |
|-----|----------|---------|
|sale_type	|optional|特价类型（请参考旅游攻略接口文档）|
|main_dept	|optional|出发地（可用值会动态变化，详询相关开发人员）|
|main_type	|optional|目的地（大类）（同上）|
|sub_type	|optional|目的地（子）（同上）|
|s_dept_time	|optional|出发时间（同上）|
|mddid | optional| 目的地id, 传该字段表示“当地”下的特价|
|mddname| optional| 目的地名字|

### [17] BANNER专题列表（首页底部）

### [18] POI榜单详情

| 设备|地址|
|---|---|
| App|http://m.mafengwo.cn/nb/public/sharejump.php?type=18&id=1448|
| web|http://www.mafengwo.cn/jd/{mddid}/{$id}.html|
| H5 |http://m.mafengwo.cn/jd/{mddid}/{$id}.html|

----

| 参数 | 是否必选| 参数说明 |
|-----|----------|---------|
|id	|required|专题id|

### [19] 目的地问答列表

| 设备|地址|
|---|---|
| App|http://m.mafengwo.cn/nb/public/sharejump.php?type=19|
| web|http://www.mafengwo.cn/wenda/area-{$mddid}.html|
| H5 |http://m.mafengwo.cn/wenda/area-{$mddid}|

---

| 参数 | 是否必选| 参数说明 |
|-----|----------|---------|
|mddid	|optional|目的地id（为空时默认查询“问达人”全部问答数据）|
|mddname		|optional|目的地名称（用于页面显示）|
|filtertype		|optional|筛选类型（用于页面筛选条件过滤，目前type对照结构：全部：0，最新发布：1，待回答问题： 2，最多有用：4，有金牌的回答：5）|

### [20] 问题详情页

| 设备|地址|
|---|---|
| App|http://m.mafengwo.cn/nb/public/sharejump.php?type=20&id={$id}|
| web|http://www.mafengwo.cn/wenda/detail-{$id}.html|
| H5 |http://m.mafengwo.cn/wenda/detail-{$id}.html|

---

| 参数 | 是否必选| 参数说明 |
|-----|----------|---------|
|id	|required|提问id|

### [21] 回答的追问列表页

| 设备|地址|
|---|---|
| App|http://m.mafengwo.cn/nb/public/sharejump.php?type=21&aid={$aid}|

----

| 参数 | 是否必选| 参数说明 |
|-----|----------|---------|
|aid	|required|回答id|
|quid	|optional|提问者uid|
|qid	|optional|问题id|

### [22] 回答的评论列表页

| 设备|地址|
|---|---|
| App|http://m.mafengwo.cn/nb/public/sharejump.php?type=22&aid={$aid}|

----

| 参数 | 是否必选| 参数说明 |
|-----|----------|---------|
|aid  |required|回答id|
|quid	|optional|提问者uid|
|qid	|optional|问题id|

### [23] 提问搜索结果列表

| 设备|地址|
|---|---|
| App|http://m.mafengwo.cn/nb/public/sharejump.php?type=23&mddid={$mddid}&tagid={$tagid}|

----

| 参数 | 是否必选| 参数说明 |
|------|----------|---------|
|mddid	|optional|目的地id|
|keyword|optional|如果tagid存在，则作为tagname|
|tagid	|optional|tagid|

### [24] 目的地图片列表(支持PUSH)

| 设备|地址|
|---|---|
| App|http://m.mafengwo.cn/nb/public/sharejump.php?type=24&mddid={$mddid}|
| web|http://www.mafengwo.cn/photo/mdd/{$mddid}.html/|
| H5 |http://m.mafengwo.cn/photo/mdd/{$mddid}.html|

----

| 参数 | 是否必选| 参数说明 |
|-----|----------|---------|
|mddid	|required|目的地id|
|mddname		|optional|目的地名称|

### [25] 个人中心(当前用户/其他用户)

| 设备|地址|
|---|---|
| App|http://m.mafengwo.cn/nb/public/sharejump.php?type=25&uid={$uid}|
| web|http://www.mafengwo.cn/u/{$uid}.html/|
| H5 |http://m.mafengwo.cn/user/?id={$uid}|

----

| 参数 | 是否必选| 参数说明 |
|-----|----------|---------|
|uid	|optional|如果不传则为当前用户|
|uname		|optional|默认显示用户名|

### [26] 私信对话页面(支持PUSH)

| 类型|地址|
|---|---|
| App|http://m.mafengwo.cn/nb/public/sharejump.php?type=26&fromid={$uid}|
| web|http://www.mafengwo.cn/msg/sms.php|
| m|暂无 用web|


----

| 参数 | 是否必选| 参数说明 |
|-----|----------|---------|
|fromuid	|required|对话的用户的id|
|fromuname		|optional|对话人的名字|
|with_push|required|1支持 push,0或空不支持????|

### [27] 酒店订单列表页

| 类型|地址|
|---|---|
| App|http://m.mafengwo.cn/nb/public/sharejump.php?type=27|
| web|http://www.mafengwo.cn/hotel/order.php|
| m|暂无 用web|


----

| 参数 | 是否必选| 参数说明 |
|-----|----------|---------|
|refresh|optional| 0 非强制刷新  1 强制刷新 |

### [28] 个人足迹

| 类型|地址|
|---|---|
| App|http://m.mafengwo.cn/nb/public/sharejump.php?type=28|
| web|http://www.mafengwo.cn/path/{$uid}.html|
| m|暂无 用web|


----

| 参数 | 是否必选| 参数说明 |
|-----|----------|---------|
|uid	|optional|如果为空,代表当前登录用户|
|uname		|optional|默认显示的用户名|

### [29] 个人点评列表

| 类型|地址|
|---|---|
| App|http://m.mafengwo.cn/nb/public/sharejump.php?type=29|
| web|http://www.mafengwo.cn/path/{$uid}.html|
| m|暂无 用web|

----
| 参数 | 是否必选| 参数说明 |
|-----|----------|---------|
|uid	|optional|如果为空,代表当前登录用户|
|uname	|optional|默认显示的用户名|

### [30] 游记评论列表

| 类型|地址|
|---|---|
| App|http://m.mafengwo.cn/nb/public/sharejump.php?type=30&id={$id}|
| web|http://www.mafengwo.cn/i/{$id}.html|
| m|http://m.mafengwo.cn/mdd/reply.php?id={$id}|

----
| 参数 | 是否必选| 参数说明 |
|-----|----------|---------|
|id	|required| 游记id|

### [31] 自由行订单列表 

| 类型|地址|
|---|---|
| App|http://m.mafengwo.cn/nb/public/sharejump.php?type=31|
| web|http://www.mafengwo.cn/sales/order.php|
| m|http://m.mafengwo.cn/sales/order.php|

----
| 参数 | 是否必选| 参数说明 |
|-----|----------|---------|
|refresh|optional| 0 非强制刷新  1 强制刷新 |

### [32] 常见问题列表 

| 类型|地址|
|---|---|
| App|http://m.mafengwo.cn/nb/public/sharejump.php?type=32|
| web||
| m||

----
### [33]每日打卡页

| 类型|地址|
|---|---|
| App|http://m.mafengwo.cn/nb/public/sharejump.php?type=33|
| web||
| m||

----
### [34]我的优惠券

| 类型|地址|
|---|---|
| App|http://m.mafengwo.cn/nb/public/sharejump.php?type=34&tip={$tip}|
| web||
| m||

| 参数 | 是否必选| 参数说明 |
|-----|----------|---------|
|tip	|optional| 领取提示|
|title	|optional| 领取标题|
|channel_icon	|optional| 领取渠道图标icon|
* 传tip就可以显示领取优惠券的提示信息

----
### [35]玩穿越

| 类型|地址|
|---|---|
| App|http://m.mafengwo.cn/nb/public/sharejump.php?type=35|

----
### [36]查目的地

| 类型|地址|
|---|---|
| App|http://m.mafengwo.cn/nb/public/sharejump.php?type=36|
| web||
| m||
* 原“查找”页

----
### [37]tab页

| 类型|地址|
|---|---|
| App|http://m.mafengwo.cn/nb/public/sharejump.php?type=37&name={$name}|
| web||
| m||

| 参数 | 是否必选| 参数说明 |
|-----|----------|---------|
|name|required| tab的名称|

* 跳到tab页指定页面：name支持：
* ios >= v7.0.0, android >= 6.0.0 包括 “discovery”，“local”，“mall”，“mine”

----
### [38]每日游记

| 类型|地址|
|---|---|
| App|http://m.mafengwo.cn/nb/public/sharejump.php?type=38|
| web||
| m||

----
### [39] 子目的地列表

| 类型|地址|
|---|---|
| App|http://m.mafengwo.cn/nb/public/sharejump.php?type=39&mddid={$mddid}|
| web|
| m|

| 参数 | 是否必选| 参数说明 |
|-----|----------|---------|
|mddid	|required| 目的地id|

----
### [40] 周边目的地列表

| 类型|地址|
|---|---|
| App|http://m.mafengwo.cn/nb/public/sharejump.php?type=40&mddid={$mddid}|
| web|
| m|

| 参数 | 是否必选| 参数说明 |
|-----|----------|---------|
|mddid	|required| 目的地id|

----
### [41] 发现专题列表

| 类型|地址|
|---|---|
| App|http://m.mafengwo.cn/nb/public/sharejump.php?type=41&id={$topicId}&style={$style}|
| web|
| m|

| 参数 | 是否必选| 参数说明 |
|-----|----------|---------|
|id	|required| 专题id|
|style	|required| 专题样式(v7.0.0:支持square,sales,notes,tops_list,四种)|
|title	|required| 专题标题|

----
### ~~[1000]自由行首页~~

| 类型|地址|
|---|---|
| App|http://m.mafengwo.cn/nb/public/sharejump.php?type=1000|
| web||
| m||

| 参数 | 是否必选| 参数说明 |
|-----|----------|---------|

----
### [1001]自由行目的地

| 类型|地址|
|---|---|
| App|http://m.mafengwo.cn/nb/public/sharejump.php?type=1001|
| web||
| m||

| 参数 | 是否必选| 参数说明 |
|-----|----------|---------|
----
### [9]自由行产品详情（支持push，和之前的9保持一致）
| 类型|地址|
|---|---|
| App|http://m.mafengwo.cn/nb/public/sharejump.php?type=9&id={$id}|
| web|http://www.mafengwo.cn/sales/{$sales_id}.html|
| m|http://m.mafengwo.cn/sales/{$sales_id}.html|

| 参数 | 是否必选| 参数说明 |
|-----|----------|---------|
|id	|required| 产品id|

----
### [1003]自由行提交订单

| 类型|地址|
|---|---|
| App|http://m.mafengwo.cn/nb/public/sharejump.php?type=1003&saleid={$saleid}|
| web|http://www.mafengwo.cn/sales/booking.php?id={$sales_id}&inventory_id={$c_id}&amount={$amount}&room_num={$room_num}|
| m|http://m.mafengwo.cn/sales/booking.php?id={$sales_id}.html|

| 参数 | 是否必选| 参数说明 |
|-----|----------|---------|
|saleid	|required| 产品id|

----
### [1004]自由行确认支付

| 类型|地址|
|---|---|
| App|http://m.mafengwo.cn/nb/public/sharejump.php?type=1004&tradeid={$tradeid}|
| web||
| m||

| 参数 | 是否必选| 参数说明 |
|-----|----------|---------|
|tradeid	|required| 订单id|

----
### [1006]自由行搜索结果

| 类型|地址|
|---|---|
| App|http://m.mafengwo.cn/nb/public/sharejump.php?type=1006&keyword={$keyword}&key={$key}&hide_search={hide_search}|
| web||
| m||

| 参数 | 是否必选| 参数说明 |
|-----|----------|---------|
|keyword	|required&optional| 搜索关键字|
|key	|required&optional| 搜索键|
|hide_search	|optional| 是否隐藏搜索bar,1为隐藏，0为显示，不传则默认显示|
重要：keyword和key至少有一个，若同时存在优先处理key，
keyword更偏重于用户主动发起的搜索 比如7天5晚，中秋，
key更偏重于像目的地页过来的搜索 我们必须对其具有相同keyword的关键词进行区分，比如mddid.
若只有key，因为客户端需要填充标题（hide_search=1）或者搜索框(hide_search=0)，此时请求返回参数中应该含有title，
则用此title填充标题或者搜索框。

支持举例：
http://m.mafengwo.cn/nb/public/sharejump.php?type=1006&key=10030
http://m.mafengwo.cn/nb/public/sharejump.php?type=1006&key=10030&hide_search=1
http://m.mafengwo.cn/nb/public/sharejump.php?type=1006&keyword=%E6%99%AE%E5%90%89%E5%B2%9B
http://m.mafengwo.cn/nb/public/sharejump.php?type=1006&keyword=%E6%99%AE%E5%90%89%E5%B2%9B&hide_search=1

----
### [1007]自由行产品列表(注意此jump支持可变参数)

| 类型|地址|
|---|---|
| App|http://m.mafengwo.cn/nb/public/sharejump.php?type=1007&title={$title}&key={$key}|
| web||
| m||

| 参数 | 是否必选| 参数说明 |
|-----|----------|---------|
|title	|required| 列表标题|
|key	|optional| 列表键值|
|其他可变参数|optional|其他可变参数|


----
###注意事项
* 北京攻略的链接	http://m.mafengwo.cn/nb/public/sharejump.php?type=1&id=29&title=%e5%8c%97%e4%ba%ac
	
* 参数要做urlencode
* 参数列表中的参数一旦定义，就不允许再变动，只可追加参数，不可删除和调整参数顺序
	
* pc 攻略下载页	http://www.mafengwo.cn/gonglve/mdd-{mddid}.html
* 手机app下载页	http://m.mafengwo.cn/app/
* 专题页面	http://www.mafengwo.cn/mobile/travelguidemdd/theme_html.php?id={id}
* 特价详情页	http://m.mafengwo.cn/sales/info.php?id={id}