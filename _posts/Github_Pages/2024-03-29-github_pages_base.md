---
title: GitHub Pages简单介绍
date: 2024-03-29
tags: [jekyll, github,web]
pinned: true
---

GitHub Pages 能够部署静态网页(HTML,CSS,JavaScript构成的网页), 也可以构建Jekyll主题的网页。

- 首先创建一个Github账号

- [Quickstart for GitHub Pages](https://docs.github.com/en/pages/quickstart) 教你创建一个 `<username>.github.io` 仓库，并将该仓库部署为网页。这样部署的网页
将以`https://<username>.github.io`为网址，以该仓库内的README.md文件作为首页。当然这只是部署一个最最简单的网页，网页的内容为README.md内容，样式为Github渲染`.md`文件的样式。

- 真实的网页以是由HTML,CSS,JavaScript各种文件构成的，能够自己定义内容和样式。如果你有这样的网页文件，可以直接将网页文件上传到`<username>.github.io` 仓库，GitHub能够部署然后以`index.html`作为首页（GitHub会寻找index.html, index.md, or README.md文件作为首页）。但是以该方式布置的网页不便于内容添加，毕竟写原生的HTML文件和样式CSS文件也是一件费时费力的事情。(当然如果你使用React或者Vue框架等，使用这些框架对应的构建网页之后，会生成dist文件夹，将该文件夹内容上传到该仓库也能完成部署。)

- Jekyll(a static site generator with built-in support for GitHub Page)对于一个个人博客，我需要能够自己定义样式，但样式基本固定，博客内容使用相同的样式就可以了。但是需要不断的为博客添加新的内容，并希望将时间放在写作上而不是样式设置上，那么使用[Jekyll](https://jekyllrb.com/)主题将是一个很好的选择。使用Jekyll定义的规则，我们能够自己设置好网页的样式，之后只需要提交`.md`文件来补充网站内容。GitHub能够渲染Jekyll主题仓库，将其转换为静态网页然后实现部署。
    >  当选择从一个分支部署你的网站(而不是使用Workflow自定义一个静态网页生成器)， GitHub Pages默认使用Jekyll来构建你的网站，如果不想使用Jekyll来构建网站请在你发布源码的根目录下创建一个.nojekyll空文件。

  [Jekyll介绍]({{ '/2024/jekyll_base.html' | prepend: site.baseurl }})

- 你还可以自己创建一个workflow
    https://docs.github.com/en/actions


