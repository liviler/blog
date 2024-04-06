---
title: Jekyll简单介绍
date: 2024-04-01
tags: [jekyll]
excerpt_separator: <!--  -->
---

Jekyll是GitHub内建支持的静态网页生成器(static site generator), 支持Markdow和Liquid语言,
[see](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/about-github-pages-and-jekyll).
<!--  -->
## 使用Jekyll提供的主题生成网页
[see](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/creating-a-github-pages-site-with-jekyll)
### 安装环境
- 首先安装好Ruby（https://www.ruby-lang.org/en/documentation/installation/ 当前版本的Ruby也会安装包管理工具gem和bundle，
- 然后安装Jekyll(https://jekyllrb.com/docs/installation/).

### 使用Jekyll创建初始的Jekyll项目
- 进入你的工作目录，使用jekyll初始化一个jekyll项目
```bash
jekyll new --skip-bundle .
# Creates a Jekyll site in the current directory
```
- 打开Gemfile文件，注释掉`gem "jekyll"`,添加`github-pages`：
```bash
gem "github-pages", "~> GITHUB-PAGES-VERSION", group: :jekyll_plugins
```
- 重新安装依赖包
```bash
bundle install
```
- 另外还可以在`_config.yml`中修改一些设置

### 在本地测试Jekyll项目
```bash
bundle exec jekyll serve
```
Ruby 3.0以后版本由于没有自动安装webrick会出现报错，运行`bundle add webrick` 安装webrick。然后再次`bundle exec jekyll serve`，访问http://localhost:4000
查看网页。

### 添加内容
#### 添加Page
在项目的根目录创建你想要的`PAGE_NAME.md`(根据用途给一个有意义的名字),然后在文件前面添加YAML头:
```YAML
layout: page
title: "PAGE-TITLE"
permalink: /URL-PATH
```
通过这样添加页面将可以通过https://username.github.io/URL-PATH 访问.
注意如果在permalink写成这样
```YAML
layout: page
title: "PAGE-TITLE"
permalink: /URL-PATH/
```
在编译的时候会在`_site`生成一个`URL-PATH`文件夹,里面放一个`index.html`.
#### 添加Post
在`_posts`目录下创建你想要的`YYYY-MM-DD-NAME-OF-POST.md`文件,`YYYY-MM-DD`代表时间,`DD-NAME-OF-POST`代表文件的名字.然后在文件开头添加YAML头:
```YAML
layout: post
title: "POST-TITLE"
date: YYYY-MM-DD hh:mm:ss -0000
categories: CATEGORY-1 CATEGORY-2
```
### 更改主题
在`_config.yml`文件中修改`theme: jekyll-theme-THEME-NAME`这一项,将`THEME-NAME`修改为[Github支持的主题](https://pages.github.com/themes/).

要使用放在GitHub上的Jekyll主题,使用`remote_theme: THEME-NAME`项, 将`THEME-NAME`换成该主题仓库在README文件中告诉你的名称.

你可以自己[设置CSS样式文件](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/adding-a-theme-to-your-github-pages-site-using-jekyll#customizing-your-themes-css)来更改网页样式, 以及[设置HTML文件](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/adding-a-theme-to-your-github-pages-site-using-jekyll#customizing-your-themes-html-layout)来更改网页布局


## 自定义样式生成网页
觉得GitHub提供的主题不够好看?那么,学习如何利用Jekyll定制一个自己喜欢样式的网页吧!\\
[Jekyll教程]({{ '/2024/jekyll_tutorial.html' | prepend: site.baseurl }})

## 将网页发布到Github上
