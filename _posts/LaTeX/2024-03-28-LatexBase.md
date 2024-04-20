---
title: Latex基础
date: 2024-03-28
tags: [latex]
---
在Overleaf：[https://www.overleaf.com/learn](https://www.overleaf.com/learn) 上给了一个全面的关于Latex的介绍。

# 基本框架代码
# 序言(preamble)
## documentclass
```latex
\documentclass[12pt, letterpaper]{article}
```

`\documentclass[...]{...}`：`{...}`定义文档类型(可用类型: [https://www.ctan.org/topic/class](https://www.ctan.org/topic/class))，`[...]`中参数配置该文档类型，各参数之间用逗号隔开。例如`\documentclass[12pt, letterpaper]{article}`:
* 12pt定义字体大小。默认字体大小为10pt(10 point Times Roman font),其他可设9pt,11pt,12pt...
* letterpaper定义页面大小。其他可设a4paper,legalpaper...([more paper size](https://www.overleaf.com/learn/latex/Page_size_and_margins#Reference_guide))
* article定义以论文(paper)形式排版。

## title, author, data
```latex
\documentclass[12pt, letterpaper]{article}
\title{My first LaTeX document}
\author{Hubert Farnsworth\thanks{Funded by the Overleaf team.}} % \thanks 可以写一些感谢信息
\date{August 2022} % \date{\today} 表示当前日期
```
 添加标题，作者，日期等信息。将上面内容在preamble中写好之后，要在body当中使用`\maketitle`来展示这些信息。

## package
通过使用其他包，可以实现更多的排版功能。使用以下命令可以导入其他包：
``` latex
\usepackage[options]{somepackage}
```
其中`[options]`使用改包并提供的参数，`somepackage`是包的名称。当使用改命令的时候，LaTex会寻找相关的`somepackage.sty`文件，
在该文件中定义了一些命令可供用户使用。
### CTAN
Comprehensive TeX Archive Network([CTAN](https://www.ctan.org/)) 网站中存LaTex的各种包及其相关文档，可在该网站上进行搜索。
### Tex Live
[Tex Live](https://tug.org/texlive/) 包含了
- CTAN的大部分包(有一些包由于过时，许可问题以及具有平台依赖性等原因未被包含进去)
- LaTex 相关字体
- 其他软件，包括各编译器

所以，对于用户来说，只要安装Tex Live就配置好LaTex所需要的环境!不过Tex Live每一年更新一次，所以最新的包可能不会被包括进去。
# 主体(body)
介于`\begin{document}...\end{document}`之间的部分。

## 摘要
使用`\begin{abstract}..\end{abstract}`来添加摘要。

## 段落与换行
在源码中按两次回车键，使得两段文字之间差一个空白行，就能够实现另起一段。使用`\\`或者`\newline`能够换行。
注意新的段落会默认的有缩进，而换行不会有缩进。

## 章节
LaTex支持下面这些分段命令：
- \part{part}
- \chapter{chapter}
- \section{section}
- \subsection{subsection}
- \subsubsection{subsubsection}
- \paragraph{paragraph}
- \subparagraph{subparagraph}

但是不同的文档类型支持不同的分段命令，例如`\report`和`\chapter`命令只有`report`和`book`文档类型支持。

## 更改文字样式
* `\textbf{...}` 加粗
* `\textit{...}` 意大利斜体
* `\underline{...}` 下划线
* `\emph{...}` 普通文本变为意大利斜体，意大利斜体变为普通文本

## 添加图片
```latex
documentclass{article}
\usepackage{graphicx}
\graphicspath{{images/}}
 
\begin{document}

\begin{figure}[h]
    \centering
    \includegraphics[width=0.75\textwidth]{mesh}
    \caption{A nice plot.}
    \label{fig:mesh1}
\end{figure}
 
As you can see in figure \ref{fig:mesh1}, the function grows near the origin. This example is on page \pageref{fig:mesh1}.

\end{document}
```

## 添加列表
各种列表，查看[https://www.overleaf.com/project/661b9ec36615f5a383776d45](https://www.overleaf.com/project/661b9ec36615f5a383776d45)

## 创建表格
```latex
\begin{center}
 \begin{tabular}{||c c c c||} 
 \hline
 Col1 & Col2 & Col2 & Col3 \\
 \hline\hline
 1 & 6 & 87837 & 787 \\ 
 \hline
 2 & 7 & 78 & 5415 \\
 \hline
 3 & 545 & 778 & 7507 \\
 \hline
 4 & 545 & 18744 & 7560 \\
 \hline
 5 & 88 & 788 & 6344 \\ [1ex] 
 \hline
\end{tabular}
\end{center}
```
`\begin{center}...\end{center}`使得生成的表格居中对齐；`\begin{tabular}{||cccc||}...\end{tabular}`是默认的LaTex创建表格的方法；`|`表示创建给表格创建垂直分隔线，`c`表示表格单元中的文字居中对齐(`l`左对齐,`r`右对齐)；`\hline`表示插入横线；`&`是同一行表格单元之间的分隔符；`\\`是一行的结束符号。

手动写上面代码来创建表格会过于繁琐，可以使用在线工具生成表格: [https://www.tablesgenerator.com/](https://www.tablesgenerator.com/)

上面只是创建一个表格，若要为表格添加Caption以及想要引用表格，那么需要表格环境:
```latex
Table \ref{table:data} shows how to add a table caption and reference a table.
\begin{table}[h!]
\centering
\begin{tabular}{||c c c c||} 
 \hline
 Col1 & Col2 & Col2 & Col3 \\ [0.5ex] 
 \hline\hline
 1 & 6 & 87837 & 787 \\ 
 2 & 7 & 78 & 5415 \\
 3 & 545 & 778 & 7507 \\
 4 & 545 & 18744 & 7560 \\
 5 & 88 & 788 & 6344 \\ [1ex] 
 \hline
\end{tabular}
\caption{Table to test captions and labels.}
\label{table:data}
\end{table}
```
`\begin{table}[h!]...\end{table}`是表格环境，其中`[h!]`定义表格环境创建的表格在页面中的位置，`\centering`是表格的对齐方式，`\caption{...}`创建表格标题， `\label{...}`为表格添加一个标签，以便被`\ref{...}`引用。
## 书写公式
### 行内公式(inline)
使用` \( ... \)`, `$ ... $` 和 `\begin{math} ... \end{math}`可以书写行内公式：
```latex
\documentclass[12pt, letterpaper]{article}
\begin{document}
\begin{math}
E=mc^2
\end{math} is typeset in a paragraph using inline math mode---as is $E=mc^2$, and so too is \(E=mc^2\).
\end{document}
```
### display
`\begin{equation}...\end{equation}`书写带有编号的公式，使用`[\...\]`  `$$...$$` `\begin{displaymath}...\begin{displaymath}`书写不带有编号的公式。
`amsmath`包提供的`\begin{equation*}...\begin{equation*}`也能编写没有编号的公式。

# 进阶
## 页面布局
> [Page size and margins](https://www.overleaf.com/learn/latex/Learn_LaTeX_in_30_minutes)

### [geometry package](https://ctan.org/pkg/geometry?lang=en)
使用`geometry`包可以对页面的布局进行调整:
```
\usepackage[legalpaper, landscape, margin=2in]{geometry}
```
也可以下面方式使用(使用`\geometry`来设置布局情况)：
```
\usepackage{geometry}
\geometry{legalpaper, landscape, margin=2in}
```
legalpaper 是页面大小，landscape 是表示页面方向， margin调整边距。

更多的调节参数查看： [geometry package layout parameters](https://www.overleaf.com/learn/latex/Page_size_and_margins#Using_the_geometry_package_layout_parameters)
### layout package
使用`layout`包可以可视化文档的当前布局情况，然后使用`layout`和`layout*`命令来查看布局的图像（`layout*`展示修改后的布局情况）。