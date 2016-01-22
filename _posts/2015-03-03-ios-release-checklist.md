---
layout: page
title: "工程师[CheckList]"
category: ios
date: 2015-03-03 18:41:36
---

### 提交苹果ITC前的check流程

- 确定版本号（Version, Build）
- 确定所有分支都已经合并到develop_new
- 从develop_new创建新分支release_appname_appversion (所有对于该版本的bug修复 都提交至此 持续merge到develop_new和master分支)
- 
- 将代码checkout到release_appname_appversion分支，run一下所有功能
- umeng在线参数设置, 将`hideAppWallVer`设置为要审核的版本号(不带build号的版本号)，如 6.5.0
- 检查xcode的配置，Edit Scheme->archieve对应的是否是Release的configuration![edit-scheme]({{site.imageurl}}/edit-scheme.png)
- 选择正确的证书，build并提交itc
- 在itc看到build的包后，创建test-flight的内部测试的包，相关人员收到连接后安装并使用主要功能，看是否有问题
- test-flight的包查看是否有应用墙推荐，如果有则说明没有配置正确的umeng在线参数，这样苹果审核会拒掉
- gitlab上创建相应的tag
- 打越狱渠道包