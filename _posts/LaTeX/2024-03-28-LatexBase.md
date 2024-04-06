---
title: Latex基础
date: 2024-03-28
tags: [latex]
---
在Overleaf： https://www.overleaf.com/learn 上给了一个全面的关于Latex的介绍。

# 基本框架代码
```latex
\documentclass[12pt, letterpaper]{article}


```

`\documentclass[...]{...}`，`{...}`定义文档类型(其他类型: https://www.ctan.org/topic/class)，`[...]`中参数配置该文档类型。例如`\documentclass[12pt, letterpaper]{article}`:
* 12pt定义字体大小。默认字体大小为10pt(10 point Times Roman font),其他可设9pt,11pt,12pt...
* letterpaper定义页面大小。其他可设a4paper,legalpaper...
* article定义以论文(paper)形式排版。



