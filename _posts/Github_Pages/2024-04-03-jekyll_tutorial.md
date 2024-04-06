---
title: Jekyll教程
date: 2024-04-03
tags: [jekyll,tutorial]
comments: true
---
# 技能准备
1. (60min+) HTML,CSS, Javascript基础:\\
  [W3School HTML](https://www.w3school.com.cn/html/index.asp),
  [W3school CSS](https://www.w3school.com.cn/css/index.asp),
  [Runoob JavaScript](https://www.runoob.com/js/js-tutorial.html)\\
  了解CSS后,还要知道CSS的扩展语言: [Sass教程](https://www.sass.hk/docs/)
  > 网页最终还是以这三大件形式呈现的, 要想自己定制博客,至少要对这三样的作用有所了解.才能明白Jekyll到底为我们生成了什么,简化了那些操作.
  > 同时要自己定制网页,HTML和CSS是必须会的,否则只能使用别人的模板并且不知道如何基于别人模板来定制自己的样式.
2. (60min) Markdown 基本语法.
  > 了解如何使用Mardown语言书写文本
5. (30min) Liquid语言会在Jekyll书写页面及布局时候用到:\\
  [Liquid tutorial](https://shopify.github.io/liquid/), [Liquid教程](https://liquid.bootcss.com/)
  > 了解怎样使用objects,tags,filters即可
6. (15min) YAML数据格式在Jekyll 的文件头中会用到,并且Ruby的配置文件`_config.yml`也是YAML文件:\\
   [Runoob YAML入门教程](https://www.runoob.com/w3cnote/yaml-intro.html)
   > 了解YAML内数据是怎么组织的,能够看出数据键值之间的层级关系.
3. (15min) Ruby是Jekyll的运行的高级语言环境,也许要对Ruby的运行有简单的了解: \\
  Ruby的一些概念介绍: [ruby101](https://jekyllrb.com/docs/ruby-101/),
  Ruby more details: [quickstart](https://www.ruby-lang.org/en/documentation/quickstart/)\\
  > 了解`gem`,`bundle`命令;  了解`Gemfile`,`Gemfile.lock`, `_config.yml`文件的作用.
4. (15min) jekyll命令了解:\\
  [jekyll常用命令](https://jekyllrb.com/docs/usage/)
  > 了解`jekyll serve`

具备上面的技能才能更好的了解Jekyll的工作原理,但是即使对上面的一个或者多个并不熟悉,其实也可以直接看下面的教程,遇到不懂的地方再返回了解即可.

# 配置Jekyll环境
1. Jekyll 环境的[安装](https://jekyllrb.com/docs/installation/)
2. 测试Jekyll环境:[Quickstart](https://jekyllrb.com/docs/)
```bash
gem install jekyll bundler # Install the jekyll and bundler gems. 
jekyll new myblog # Create a new Jekyll site at ./myblog. 
cd myblog 
bundle exec jekyll serve # Build the site and make it available on a local server. 
# see http://localhost:4000 
# If you are using Ruby version 3.0.0 or higher.
# You may fix it by adding webrick to your dependencies: bundle add webrick
```

# 搭建Jekyll网页
你应该跟着[Step by Step Tutorial](https://jekyllrb.com/docs/step-by-step/01-setup/)的步骤去自己搭建一个Jekyll网页,了解各命令的运行以及各文件及文件夹
的作用. 以下对重要的概念进行摘要;
## gem,bundle, jekyll命令

* `gem` 是Ruby安装gem文件的命令(jekyll, bundle也算是gem)
```bash
gem install jekyll bundler # 使用gem安装jekyll和bundler
```
* `bundle` 是比`gem`更方便的gem管理工具
```bash
bundle init # 创建一个 Gemfile文件来记录gem依赖
bundle add jekyll # bundle安装jekyll,并将版本写在Gemfile文件中, 依赖关系写入Gemfile.lock文件中
bundle exec jekyll serve # 使用Gemfile中的jekyll版本运行 jekyll serve
```
* `jekyll` 是jekyll用来生成网页的命令
```bash 
jekyll build # Builds the site and outputs a static site to a directory called _site.
jekyll serve # Does jekyll build and runs it on a local web server at http://localhost:4000, rebuilding the site any time you make a change.
jekyll serve --livereload # force the browser to refresh with every change,
```

Jekyll在生成静态网页时候,其实会以执行jekyll build(jekyll server)的工作目录为根目录,保留根目录下的各目录的结构,生成静态文件并放在`_site`目录下.

## Liquid
教程:[Liquid tutorial](https://shopify.github.io/liquid/), [Liquid教程](https://liquid.bootcss.com/)\\
Liquid是一种模板语言,可以使得网页中引用变量,逻辑,以及一些功能处理.它包含3种主要成分: objects,tags,filters
### Object
使用双括号包括变量,例如使用`{%raw%}{{ page.title }}{%endraw%}`来取变量page.title表示的值.\\
更多变量:[variables](https://jekyllrb.com/docs/variables/)
### Tags
为网页定义逻辑行为
```liquid
{% raw %}
{% if page.show_sidebar %}
  <div class="sidebar">
    sidebar content
  </div>
{% endif %}
{% endraw %}
```
更多tags:[Liquid tags](https://shopify.github.io/liquid/tags/control-flow/),[Jkeyll tags](https://jekyllrb.com/docs/liquid/tags/),[plugins tags](https://jekyllrb.com/docs/plugins/tags/)

### Filters
使用具有功能的函数处理值, 使用`|`进行分割. 
```
{% raw %}
{{ "hi" | capitalize }}
{% endraw %}
```
将hi 变为 Hi.

[Liquid filters](https://shopify.github.io/liquid/filters/abs/),[Jkeyll filters](https://jekyllrb.com/docs/liquid/filters/)


### 例子
```html
---
# front matter tells Jekyll to process Liquid
---
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>Home</title>
  </head>
  <body>
    <h1>{% raw %}{{ "Hello World!" | downcase }}{% endraw %}</h1>
  </body>
</html>
```
注意要加入一个头部(就是上下两个`---`),以告诉Jekyll编译时候处理Liquid部分代码.


## Front Matter
[Runoob YAML入门教程](https://www.runoob.com/w3cnote/yaml-intro.html)\\
在你的网页文件(Markdown,HTML)开头可以添加Front Matter.
Front Matter是位于文件开头的两条`---`之间的YAML代码片段.例如你可以在该处设置变量
```yaml
---
my_number: 5
---
```
然后在页面中使用`page`来调用该变量的值:
```
{% raw %} {{ page.my_number }} {% endraw %}
```

## Layouts
在有多个网页时候可能只是网页的内容不同,而网页的布局和样式是一样的.那么可以在`_layouts`文件夹下定义布局文件,然后在你所写的页面中使用该布局文件.
例如,在`_layouts`文件中创建一个`default.html`文件:
```html
<!doctype html>
<html>
  <head>
    <meta charset="utf-8">
    <title>{% raw %}{{ page.title }}{% endraw %}</title>
  </head>
  <body>
    {% raw %}{{ content }}{% endraw %}
  </body>
</html>
```
然后在你的网页文件中使用该模板:
```html
---
layout: default
title: Home
---
<h1>{% raw %}{{ "Hello World!" | downcase }}{% endraw %}</h1>
```
这样,Jekyll在渲染时候会自动将网页渲染后的内容填充至布局文件`{% raw %}{{ content }}{% endraw %}` 所在的地方,从而生成基于`default.html`布局的网页文件.

实际上,可以多层套娃,布局文件A中也能加入Front Matter来使用布局文件B, 当使用布局文件A的网页渲染到A布局后,会继续向上渲染将渲染后的内容放到B中.

## Includes
在`_includes`目录中创建文件能够使用`{% raw %}{% include navigation.html %}{% endraw %}`将该文件中的内容复用到其他文件中.
例如,在`_includes/navigation.html`中定义了导航文件:
```html
<nav>
  <a href="/">Home</a>
  <a href="/about.html">About</a>
</nav>
```
然后在布局文件`_layouts/default.html`中使用, 该部分代码:
```html
<!doctype html>
<html>
  <head>
    <meta charset="utf-8">
    <title>{% raw %}{{ page.title }}{% endraw %}</title>
  </head>
  <body>
    {% raw %}{% include navigation.html %}{% endraw %}
    {% raw %}{{ content }}{% endraw %}
  </body>
</html>
```



## Data File
你可以将一些值以YAML, JSON, and CSV 形式存放,并将文件放在`_data`文件夹下面,然后在网页中使用这些文件中的变量.
例如创建`_data/navigation.yml`文件用以记录导航栏项的名称和对应地址:
```yaml
- name: Home
  link: /
- name: About
  link: /about.html
```
然后在网页中通过`site.data.navigation`来使用该文件中的变量值,例如将上面的`_includes/navigation.html`更改为:
```html
{% raw %}
<nav>
  {% for item in site.data.navigation %}
    <a href="{{ item.link }}" {% if page.url == item.link %}style="color: red;"{% endif %}>
      {{ item.name }}
    </a>
  {% endfor %}
</nav>
{% endraw %}
```
这样就能够通过循环的方式更方便的创建导航栏的目录项了.

## Assets
创建一个 assets文件夹,用于存放css,js,images等文件, 此文件夹中的内容将被渲染之后被复制到`_site`文件夹下.
例如创建一个`assets/css/styles.scss`文件并在其中写入样式以便在html文件中使用`<link rel="stylesheet" href="/assets/css/styles.css">`
引用该样式文件. 为了方便管理可以在`_sass`文件夹下创建样式文件然后在`assets/css/styless.scss`中导入:
1. `_sass/main.scss`创建样式:
```scss
.current {
  color: green;
}
```

2. `assets/css/styles.scss`导入样式(注入添加 Front matter告诉Jekyll从`_sass`文件夹下寻找文件):
```scss
---
---
@import "main";
```


3. 在HTML布局文件中使用样式:

```html
<!doctype html>
  <html>
    <head>
      <meta charset="utf-8">
      <title>{%raw%}{{ page.title }}{%endraw%}</title>
      <link rel="stylesheet" href="/assets/css/styles.css">
    </head>
    <body>
      {%raw%}{% include navigation.html %}{%endraw%}
      {%raw%}{{ content }}{%endraw%}
    </body>
  </html>
```


## Posts
创建`_posts`目录,在该目录下创建bolg文件, 文件必须有特定格式`PublishDate-Title.extension`. 可以创建`_layouts/post.html`来定义post布局,
然后在bolg文件中使用该布局:
`_posts/2018-08-20-bananas.md`:
```
---
layout: post
author: jill
---

A banana is an edible fruit – botanically a berry – produced by several
kinds of large herbaceous flowering plants in the genus Musa.

In some countries, bananas used for cooking may be called "plantains",
distinguishing them from dessert bananas. The fruit is variable in size,
color, and firmness, but is usually elongated and curved, with soft
flesh rich in starch covered with a rind, which may be green, yellow,
red, purple, or brown when ripe.

```

`_layouts/post.html`
  ```html
  {% raw %}
  ---
  layout: default
  ---
  <h1>{{ page.title }}</h1>
  <p>{{ page.date | date_to_string }} - {{ page.author }}</p>

  {{ content }}
  {% endraw %}
  ```

当Jekyll渲染完`_posts`文件夹中的文件时候,会在`site.posts`中记录所有的posts的信息(包括url,time等).
  ```
  {% raw %}
  ---
  layout: default
  title: Blog
  ---
  <h1>Latest Posts</h1>

  <ul>
    {% for post in site.posts %}
      <li>
        <h2><a href="{{ post.url }}">{{ post.title }}</a></h2>
        {{ post.excerpt }}
      </li>
    {% endfor %}
  </ul>
  {% endraw %}
  ```
* post.url is automatically set by Jekyll to the output path of the post
* post.title is pulled from the post filename and can be overridden by setting title in front matter
* post.excerpt is the first paragraph of content by default


## Collections
see [Collections](https://jekyllrb.com/docs/step-by-step/09-collections/)


# 更好的理解Jekyll
## _config.yml 的可配置项
* [默认配置](https://jekyllrb.com/docs/configuration/default/)
* [可以配置](https://jekyllrb.com/docs/configuration/options/)
* [配置默认的Front Matter](https://jekyllrb.com/docs/configuration/front-matter-defaults/)

## 文件的渲染
  1. 以`_`,`.`开头的文件夹默认不会被渲染
  2. Jekyll默认设置的不会被渲染的目录和文件:

      ```
          .sass-cache/
          .jekyll-cache/
          gemfiles/
          Gemfile
          Gemfile.lock
          node_modules/
          vendor/bundle/
          vendor/cache/
          vendor/gems/
          vendor/ruby/
      ```
  3. `_config.yml`的 `exclude: [DIR, FILE, ...]`里面文件和目录也不会被渲染
  4. `_config.yml`的 `include: [DIR, FILE, ...]`里面的文件或目录会被包含

  注意`include`中的优先级比`exclude`中的优先级高; 重新在`_config.yml`设置`exclude`的值,Jekyll默认设置的值将被覆盖.



## Jekyll构建流程
[see](https://jekyllrb.com/docs/rendering-process/)

## Jekyll在构建时候的目录创建原则
文件的生成目录跟[permalinks](https://jekyllrb.com/docs/permalinks/)有关. 默认情况下`permalinks:date`, 而`data`为`/:categories/:year/:month/:day/:title:output_ext`.
* 可以在`_config`文件中修改`permalink`的值以设置全局的`permalink`
* 也可以在文件的Front Matter中自定义`permalink`,此优先级比全局设定值要高.
值得注意在`_posts`中

> 因为有文件要放到某个目录下,所以才创建该目录.

## tags和categories的不同
[Tags and Categories](https://jekyllrb.com/docs/posts/#tags-and-categories)

## 各目录作用
* `_set/` 该目录存放渲染后的网页文件,作为发布网页时候的根目录.

* `_posts/` 用于放置博客内容, 里面可以用Markdown和HTML语言书写. 该目录下文件必须命名为`YEAR-MONTH-DAY-title.MARKUP`. 在`site.posts`中记录所有的posts的信息(包括url,time等). 注意`_posts`目录并不一定在项目根目录下,可以在普通目录下,例如`move/_posts/tom.md`也是会被渲染成Posts的.

* `_layouts/` 布局文件所在的位置, 里面的布局样式可以被文章在Front Matter中添加`layout: XXX`来设置, `XXX`为该目录下的布局文件名

* `_includes/` 这里面的文件可以通过`{% raw %}{% include XXX.html %}{% endraw %}`将该`XXX.html`文件中的内容复用到其他文件中去.

* `_sass/` 这里放置Sass样式文件, 其他地方可以通过`import`导入.例如`@import 'tale';`导入`_sass/`下的`tale.scss`文件样式.

* `_data/` 可以将一些值以YAML, JSON, and CSV 形式存放,并将文件放在`_data`文件夹下面,然后在网页中使用这些文件中的变量.

* `assets/` 用于放置图片,文件等.在Jekyll渲染时候,会将此文件夹复制到`_site`文件夹下, 在页面中可以通过地址`/assets/FILENAME`访问FILENAME文件.

* `_drafts/` 用以存放还未完成的文章,可以不在文件名前赋予时间.使用`jekyll serve` 或 `jekyll build`并带有`--drafts`参数可以将该文件也渲染,并以该文件的修改时间作为文件明上的时间.


# 扩展功能
## 分页(pagination)
see [Pagination](https://jekyllrb.com/docs/pagination/)\\
Jekyll通过jekyll-paginate插件支持分页功能,但是它只能对`posts`中的变量中的所有文章进行分页,不支持`tags`和`categories`的分类功能.\\
在`_config.yml`设置:
``` yaml
  paginate: 5  # 设置每页显示的文章数量
  paginate_path: "/blogs/:num/" # 设置分页的路径
```
在一个`/blogs/index.html`中引用:
```
<!-- This loops through the paginated posts -->
{% for post in paginator.posts %}
  <h1><a href="{{ post.url }}">{{ post.title }}</a></h1>
  <p class="author">
    <span class="date">{{ post.date }}</span>
  </p>
  <div class="content">
    {{ post.content }}
  </div>
{% endfor %}

<!-- Pagination links -->
<div class="pagination">
  {% if paginator.previous_page %}
    <a href="{{ paginator.previous_page_path }}" class="previous">
      Previous
    </a>
  {% else %}
    <span class="previous">Previous</span>
  {% endif %}
  <span class="page_number ">
    Page: {{ paginator.page }} of {{ paginator.total_pages }}
  </span>
  {% if paginator.next_page %}
    <a href="{{ paginator.next_page_path }}" class="next">Next</a>
  {% else %}
    <span class="next ">Next</span>
  {% endif %}
</div>
```
值得注意的是,要在一个`index.html`文件里面使用分页.例如上面不能直接创建`blogs.index`然后在里面使用分页.
## 评论(Disqus)
  使用Disqus提供的服务,可以给博客添加评论功能.
## Feed
[RSS、Atom、Feed 介绍与简单实现](https://blog.wenzhixin.net.cn/2013/11/08/rss-atom-feed-php/)


