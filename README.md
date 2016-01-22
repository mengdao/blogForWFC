# jekyll
该项目使用的的jekyll静态博客系统，模板:jekyll-docs-template

Read the docs: http://bruth.github.io/jekyll-docs-template

# 博客使用

访问地址：http://mdocs.codingview.com/

密码：mafengwo123mdocs

## categore
分别对应左边的导航栏分类，目前在用的分类有：

- 'product'   产品需求文档  
- 'entity'    业务实体描述文档
- 'data'      后台数据接口文档
- 'ios'       iOS项目文档
- 'android'   Android项目文档
- 'team'      团队相关文档
- 'help'      帮助

## 创建新文章

```
   # cd到该项目的目录下（_config.yml所在的目录）
   # ruby bin/jekyll-page $TITLE $CATEGORY, 如：
   ruby bin/jekyll-page 'this is title' 'ios'
```
创建的文章在`_posts`目录下，使用文本工具（如 Mou.app）打开即可。

### 创建'产品需求文档'文章

    ruby bin/jekyll-page 'tile is here' 'product'


### 创建'后台数据接口文档'文章
    
    ruby bin/jekyll-page 'title is me' 'data'
    
### 创建'iOS项目文档'文章
    
    ruby bin/jekyll-page 'title is me' 'ios'
    
### 创建'Android项目文档'文章
    
    ruby bin/jekyll-page 'title is me' 'android'
    
### 创建'团队相关文档'文章
    
    ruby bin/jekyll-page 'title is me' 'team'
    
### 创建'帮助'文章
    
    ruby bin/jekyll-page 'title is me' 'help'
    
    
Wiki链接：http://mdocs.codingview.com/