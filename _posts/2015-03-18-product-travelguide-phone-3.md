---
layout: page
title: "行中版"
category: product-hidden
date: 2015-03-18 16:43:32
---

## 旅游攻略_V7.0 Feature List

| Feature               | 状态 | 产品    | 设计    |iOS 客户端|Android 客户端|服务端 | 备注说明                 |   IOS设计图 | Android设计图 | 接口文档 | 
|-----------------------|----- | ------- | ------- | -------- | -------- |---------- |------------------------- |------- |------ |------ |
| [我的]新增“自由行订单”| TODO | OK,陈曦 | OK,小明 | 艳玲     |  陈雯    |李培       | “我的酒店”改为“我的订单；|[设计图🐔](http://gitlab.mafengwo.com/mingyu/travelguide-ui/tree/master/iPhone/V6.5.4/%E6%88%91%E7%9A%84%E8%AE%A2%E5%8D%95)  |[设计图🐶](http://gitlab.mafengwo.com/mingyu/travelguide-ui/blob/master/Android/v7.0.0/%E6%88%91%E7%9A%84%E8%AE%A2%E5%8D%95/order_MarkMan.png) |[自由行订单🚂]({% post_url 2015-03-27-data-sale %}#获取我的自由行订单列表) |
| [我的]新增“我的优惠券”| TODO | OK,陈曦 | OK,小明 | 艳玲     |  陈雯    |李培       |放在“我的订单”之后        |[设计图🐔](http://gitlab.mafengwo.com/mingyu/travelguide-ui/tree/master/iPhone/v7.0.0/%E6%88%91%E7%9A%84%E8%AE%A2%E5%8D%95)  |[设计图🐶](http://gitlab.mafengwo.com/mingyu/travelguide-ui/blob/master/Android/v7.0.0/%E6%88%91%E7%9A%84%E8%AE%A2%E5%8D%95/coupon_MarkMan.png) |[我的优惠券🚂]({% post_url 2015-03-27-data-coupon %})|
| [搜索]大搜索改版      | TODO | OK,陈惠 | OK,小明 | 艳玲     |  文浩    |小飞熊     |支持指定目的地内搜索      |[设计图🐔](http://gitlab.mafengwo.com/mingyu/travelguide-ui/tree/master/iPhone/v7.0.0/%E6%90%9C%E7%B4%A2)                    |[设计图🐶](http://gitlab.mafengwo.com/mingyu/travelguide-ui/tree/master/Android/v7.0.0/%E6%90%9C%E7%B4%A2) |[大搜索🚂]({% post_url 2015-04-08-data-great-searching %}) |
| [当地]新增“当地”页    | TODO | OK,陈惠 | OK,小明 | 晓峰     |  许声    |小飞熊     |导航历史记录              |[设计图🐔](http://gitlab.mafengwo.com/mingyu/travelguide-ui/blob/master/iPhone/v7.0.0/%E5%BD%93%E5%9C%B0/local-3_MarkMan.png)|[设计图🐶](http://gitlab.mafengwo.com/mingyu/travelguide-ui/tree/master/Android/v7.0.0/%E5%BD%93%E5%9C%B0) | [当地widget🚂]({% post_url 2015-04-08-data-widget %}#获取某个目的地下的Widget的种类信息) |
| [当地]雷达找周边      | TODO | OK,陈惠 | OK,小明 | 教练     |  胡伟    |小飞熊     |                          |[设计图🐔](http://gitlab.mafengwo.com/mingyu/travelguide-ui/tree/master/iPhone/v7.0.0/%E6%97%85%E8%A1%8C%E9%9B%B7%E8%BE%BE)  |[设计图🐶](http://gitlab.mafengwo.com/mingyu/travelguide-ui/tree/master/Android/v7.0.0/%E6%97%85%E8%A1%8C%E9%9B%B7%E8%BE%BE) |------ |
| [当地]新增“当地下载”  | TODO | OK,陈惠 | OK,小明 | 旻昊     |  刘笑    |小飞熊     |                          |[设计图🐔](http://gitlab.mafengwo.com/mingyu/travelguide-ui/blob/master/iPhone/v7.0.0/%E5%BD%93%E5%9C%B0/local-download.png) |[设计图🐶](http://gitlab.mafengwo.com/mingyu/travelguide-ui/blob/master/Android/v7.0.0/%E5%BD%93%E5%9C%B0/local-download.png) |------ |
| [当地]新增榜单列表    | TODO | ING,陈惠| ING,小明|          |          |小飞熊     |改为H5实现                |[设计图]|[设计图] |------ |
| [当地]我的浏览历史    | TODO | OK,陈惠 | OK,小明 |          |  许声    |小飞熊     |                          |[设计图🐔](http://gitlab.mafengwo.com/mingyu/travelguide-ui/blob/master/iPhone/v7.0.0/%E5%BD%93%E5%9C%B0/local-history.png)  |[设计图🐶](http://gitlab.mafengwo.com/mingyu/travelguide-ui/blob/master/Android/v7.0.0/%E5%BD%93%E5%9C%B0/local-history.png) |------ |
| [我的]足迹2期         | TODO | ING,王然| 排期中  | 旻昊     |  文浩    |小飞熊     |                          |[设计图]|[设计图] |------ |
| 动态下拉刷新(Android) | TODO | 教练    | OK      | 已完成   |  胡伟    |           |                          |[设计图]|[设计图] |------ |
| 大图手势缩放(Android) | TODO | 陈惠    | OK      |          |  刘笑    | 无        |                          |[设计图]|[设计图] |------ |


### MRD-大搜索改版
搜索结果页内容类型依次排序：

1. 目的地（最多1条）
2. POI(非酒店）（最多2条）
3. 酒店（最多2条）
4. 离线攻略（最多1条）
5. 问答（最多3条）
6. 游记（最多3条）
7. 用户（最多3条）

**核心指标**

搜索命中率 = 是否二次跳转/搜索次数

**日志数据**

keyword
 - 是否二次跳转
 - 每次搜索跳转（结果类型，结果ID，结果标题，命中词）

### 2.MRD-当地页面
将用户行中场景的功能做成可自定义的工具箱。

0. 本地默认：搜索框（天气+我的下载&收藏）
1. Widget：找附近
2. Widget：特色榜单
3. Widget：订酒店
4. Widget：当地游
5. Widget：我的浏览历史
6. Widget：汇率计算（TODO）

-------------详细------------
#### 关于获取定位

- 启动时检测：

        每次启动后检测是否开启定位（每天仅检测一次）
        是：获取用户经纬度 -> 根据经纬度获取所在目的地 - > 上报日志
        否：忽略

- 使用“当地”功能时检测：

        - 每次点击当地页面检测是否开启定位
        
        是：获取用户经纬度 -> 根据经纬度获取所在目的地
        - 如果 上次定位所在地 == 空 & 最新定位所在地 <> 空，则当地 = 最新定位所在地。
        - 如果 上次定位所在地 <> 最新定位所在地 & 当地 <> 最新定位所在地。说明用户切换了城市，则提示“发现你目前在东京，是否要切换到东京？（每次启动内仅提示一次） 

        否：提醒用户“定位未开启”，“请在设置-隐私-定位服务中确认”，旅游攻略是否为开启状态（每次启动内仅提示一次） 
        - 如果“上次定位所在地” == 空，则当地 = 北京
        - 如果“上次定位所在地” <> 空，则当地 = 上次定位所在地


#### 本地默认：本地搜索框

显示当前定位的目的地。切换城市，进入城市选择页

显示当地天气

显示是否有收藏（为0淡色）

显示是否已下载（本地）（为0淡色）

显示搜索框。点击进入大搜索，默认目的地参数


#### 找附近

ICON进入POI列表，默认查询参数为 我的位置+附近5km。

底部进入“雷达找周边”页面

#### 订酒店

附近酒店：我的位置经纬度 + 附近5km + 酒店POI

热门酒店：目的地ID + poi_type = 酒店

显示酒店攻略，更多进入H5 页面

#### 当地游

默认显示3条当地游产品，更多进入页面待定。

#### 我的浏览历史

记录用户所有对于详情页的浏览历史，时间+类型+页面地址。

需要记录的实体包括（POI，游记详情，问答详情页，自由行详情页，攻略页，攻略榜单页）

点击更多进入浏览详情页。

### MRD-雷达找周边
利用雷达的概念帮助用户进行基于LBS的信息搜索

用户场景：

-我想看周边的有什么好玩的

-我想看周边的有什么好玩的

搜索参数：地图范围（中心点+距离）+数据条件（POI类型）

默认条件：我的位置+5km+全部类型（非酒店类POI）

1. 搜索结果展现

1.1 地图部分：

加载状态：雷达搜寻动画

数据呈现：中心点：如果登录用户，显示用户头像；如果未登录用户，显示默认图。
数据：根据经纬度显示在圆形内，不同类型不同样式。如果是已收藏显示不同样式。（景点，美食，娱乐，购物）

数据交互：用户可点击地图ICON，切换结果呈现数据。选中态样式不同。

1.2 结果部分：

加载状态：显示搜索结果默认图

数据呈现：在底部显示POI基础信息

数据交互：点击结果进入POI页面，横滑切换页面

2. 支持更改地图范围

2.1 用户移动地图，可更改中心点

数据呈现：页面显示

PS：增加一个用户操作的触发区域


2.2 用户缩放地图，可更改中心店+半径

当中心点+半径 发生变化，用户可以重新触发搜寻。（UI上中心点显示按钮“重新搜寻”）

3. 支持更改POI类型

用户更改POI类型条件，触发重新搜寻。


**核心指标 **
**日志数据 **

### MRD-当地下载/收藏

用户场景：用户在行中会需要快捷查看当前目的地自己相关的内容，为了缩短用户使用路径。在当地页显示快捷入口。

* 当地的下载

页面呈现：进入当地页面，根据当前目的地ID 异步查询属于当前目的地的已下载的游记和攻略数量。

如果当地下载> 0, UI展现为实色，用户点击进入“杭州的下载“列表。

如果当地下载= 0, UI展现为淡色，不可点击。

* 当地的收藏

页面呈现：进入当地页面，根据当前目的地ID & 用户ID 获取POI收藏数量。

如果收藏数> 0, UI展现为实色，用户点击进入“杭州的收藏“列表。

如果收藏数= 0, UI展现为淡色，不可点击。

**核心指标 **
**日志数据 **

### MRD-自由行订单

**核心指标 **
**日志数据 **

### MRD-我的优惠券

**核心指标 **
**日志数据 **