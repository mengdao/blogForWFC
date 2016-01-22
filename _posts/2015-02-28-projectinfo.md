---
layout: page
title: "项目相关"
category: help
date: 2015-02-28 14:08:36

---

##生成工具
本博客使用__jekyll__作为生成工具，jekyll是一个简单的免费的Blog生成工具，类似WordPress。但是和WordPress又有很大的不同，原因是jekyll只是一个生成静态网页的工具，不需要数据库支持。但是可以配合第三方服务,例如Disqus。最关键的是jekyll可以免费部署在Github上，而且可以绑定自己的域名。更多请参考[jekyll官网][jkeyll_website]，[百度百科][baike_jekyll]<br/>
[baike_jekyll]:http://baike.baidu.com/link?url=T0N5PB-yOnESg9Ki8WGBnmDvBIzPL80xHkKxP8byZKO5G2OfV1CxpC53Cnipz53ah7IHLmqt0L7t8rIunkBqcq
[jkeyll_website]:http://jekyllrb.com/

##项目目录结构：
文档目录结构大致如下：<br/>
![项目目录]({{site.imageurl}}/jekyll_fileCons.png)
<br/>
|--- assets
   |--js
   |--img

|--- _plugins

*	Config:配置文件*	Draftts：草稿，为发表post*	Includes：能被混合以及匹配到layout里*	Layouts：post的模板，遵循YAML Front Matter*	Posts：动态内容，必须遵循yyyy-mm-dd-title.markup的格式*	Data:格式化过的网站数据必须放在这。 Jekyll engine 自动加载yaml file*	Site:自动生成的网站回放在这里，由jekyll自动转换*   assets：资源相关目录。其中js文件夹存放相关js文件；img文件夹存放图片资源。*   _plugins:jekyll相关插件放到此目录中，目前项目中只有jekyll-toc-generator插件
<br/>
##相关插件或功能组件
<br/>
###留言模块
留言模块采用友言。友言类似于国外的Disqus，国内因为一些GWF的问题，无法访问facebook或者twitter帐号，因此友言的社交登录模块很符合我们当前的需求，因此采用友言作为评论模块。更多详情请参考：[友言官网][uyan]<br/>
[uyan]:http://www.uyan.cc
__注意：__友言的数据存储放在其网站上，只有key相关所有者拥有管理权限。因此删除对应md文档的同时，其对应页面的留言也无法恢复。
###代码高亮模块
代码高亮部分采用了highlight.js，选择此项目是因为它有以下优点：

* 支持 71 种编程语言的语法解析；拥有 44 种样式
* 自动检测编程语言
* 同时为多种编程语言代码高亮
* 可以在 node.js 平台上运行
* 支持各种标签
* 与任何 js 框架兼容

插入代码块，对应语法如下：

\`\`\`[对应语言]<br/>
code block<br/>
\`\`\`<br/>

例如：<br/>
\`\`\`ObjectiveC<br/>
code block<br/>
\`\`\`<br/>

更多内容请参考[highlight.js官网][highlight]
[highlight]:https://highlightjs.org/

###搜索模块
站内搜索模块采用了tinySou，因为tinySou具有：

- 全文搜索，实时索引。可以轻松实现全文搜索功能。且其对中文优化，支持拼音搜索。
- 友好的suggestion以及对应的跳转功能
- 搜索分析与可视化，方便更好的了解我们的搜索行为。
- 据说系统架构很稳定

__注意:__ tinySou自动的索引建立（即爬虫频率）为一天一次。如果有需求可以登录管理平台进行手动建立索引。删除博客内容并不会清除对应的索引（tinySou的策略）。所以索引数据库只增不减，如果有特殊需求，需要到后台管理模块手动删除对应索引。<br/>
更多内容请参考[tinysou官网][tinysou]
[tinysou]:http://tinysou.com/

###自动正文索引模块
自动正文索引模块采用的是jekyll-toc-generator插件。该插件会根据正文结构（需要符合markdown文档结构或者html文档结构）生成索引table，并添加到正文页面。可以对其进行自定义，本文档系统已经根据xiaofeng的要求进行过定制。<br/>
默认每个文档都会生成文档结构目录，采用的是Table of Content Generator插件。如果不想在文档中生成该目录，可以在对应md文档头部加上 __noToc: true__<br/>
更多内容请参考[jekyll-toc-generator项目主页][jekyll-toc-generator]
[jekyll-toc-generator]:https://github.com/dafi/jekyll-toc-generator
