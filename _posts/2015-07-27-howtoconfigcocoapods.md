---
layout: page
title: "如何配置CocoaPods"
category: ios
date: 2015-07-27 19:35:03
noToc: true

---
本教程仅针对<b>IndepTravel-iOS-Cocoapods</b>项目
<br/>
通用教程请参考：
[CocoaPods安装和使用教程][instructionsOfCocoaPods]
 [instructionsOfCocoaPods]:http://code4app.com/article/cocoapods-install-usage
###步骤如下：


- 从Git上check代码到本地

- 配置CocoaPod:<br/>
  <b>$ gem sources --remove https://rubygems.org/</b> //等有反应之后再敲入以下命令 <br/>
  <b>$ gem sources -a http://ruby.taobao.org/</b><br/>
- 验证：<br/>
   为了验证你的Ruby镜像是并且仅是taobao，可以用以下命令查看：<br/>
	<b>$ gem sources -l </b> <br/>
只有在终端中出现下面文字才表明你上面的命令是成功的：<br/>
\*\*\* CURRENT SOURCES \*\*\*  http://ruby.taobao.org/ 

- 安装cocoaPods：<br/>
	<b>$ sudo gem install cocoapods -v 0.37.2</b>
- 终端进入项目文件下<b>"IndepTravel-iPhone”</b>

- <b>$ pod install</b>（或者pod install --no-repo-update）

- 等，等，等，等...

- 编译项目即可