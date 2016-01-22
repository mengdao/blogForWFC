---
layout: default
title: "入门文档"

---

# 操作指引
-------------

###新建文档方法：<br/>
  Terminal - 项目根目录：<br/>  `ruby bin/jekyll-page title category [filename] [--edit]`<br/> 
e.g.: `ruby bin/jekyll-page titleName help`<br/>  
__注意__：此时最好指定__title__为__英文__，fileName会自动转为英文。如果有需要，在对应`_post`文件夹下将对应md文件的title改为中文即可。<br/> 
__category__目前有__data,iOS,android,help__四种类型
###正文部分
正文部分根据markdown语法编辑文件即可。具体语法参见[markdown语法指南][markdown-Grammer]
 [markdown-Grammer]:help/intro.html### 插入图片：在根目录建立assets文件夹（已有）,然后依照md的语法来进行图片调用,语法如下：<br/><span>![描述]\(\{\{site.imgurl\}\}/imageName.jpg)</span><br/>
其中，<span>\{\{site.imageurl\}\}</span>定位到图片资源根目录，即assets/img目录下<br/>
__注意：__图片资源请放到assets/img目录下才能按上述方法进行调用。
###插入代码快并使其高亮
对应语法如下：

\`\`\`[对应语言]<br/>
code block<br/>
\`\`\`<br/>


例如：<br/>
\`\`\`ObjectiveC<br/>
code block<br/>
\`\`\`<br/>
高亮效果如下：<br/>

```ObjectiveC
#import <UIKit/UIKit.h>
#import "Dependency.h"

@protocol WorldDataSource
@optional
- (NSString*)worldName;
@required
- (BOOL)allowsToLive;
@end

@interface Test : NSObject <HelloDelegate, WorldDataSource> {
  NSString *_greeting;
}
@property (nonatomic, readonly) NSString *greeting;
- (IBAction) show;
@end
@implementation Test

@synthesize test=_test;

+ (id) test {
  return [self testWithGreeting:@"Hello, world!\nFoo bar!"];
}

- (void) dealloc {
  [_greeting release];
  [super dealloc];
}

@end
```
目前支持的高亮语言可以参考[hightlight的在线demo][hightlight]
[hightlight]:https://highlightjs.org/static/demo/

###自检方法：<br/>
1.配置jekyll运行环境，步骤如下（进入终端）:

- $ gem install jekyll
- $ jekyll new my-awesome-site
- $ cd my-awesome-site
- /my-awesome-site $ jekyll serve
- 打开浏览器，输入<b>http://localhost:4000</b>进行访问

2.如果发现输入<b>jekyll serve</b>后出现错误，根据具体错误进行排查即可。

### 注意

- category支持中文分类，只要在config.yml中添加即可。在config.yml的修改上__一定要小心引号__，是__竖直__的引号，而非中文引号。
- 默认每个文档都会生成文档结构目录，采用的是Table of Content Generator插件。如果不想在文档中生成该目录，可以在对应md文档头部加上 __noToc: true__
- 留言模块：友言 数据存储在网络上,可以使用常见社交应用进行登录。