---
title: Markdown简单介绍
date: 2019-06-02
tags: [markdown,tutorial]
pinned: true
comment: true
---

>*Markdown*初学习,记录笔记,以供之后查询参考。  
>若文章有误，望以指正。
+ [1.标题](#1)
+ [2.引用区块](#2)
+ [3.代码块](#3)
+ [4.注释](#4)
+ [5.字体、颜色和字号](#5)
+ [6.斜体和加粗](#6)
+ [7.换行](#7)
+ [8.分割线](#8)
+ [9.删除](#9)
+ [10.首行缩进](#10)
+ [11.表格](#11)
+ [12.序列](#12)
+ [13.超链接](#13)
+ [14.图片](#14)
+ [15.图片链接](#15)
+ [16.公式](#16)
+ [17.锚点](#17)
<BR>
<BR>
<BR>
<BR> 
<BR>
***
## <a id="1">1.标题</a>
Markdown的标题用 # 来： `# 文本`  
每次一级多加一个`#`  ,但是注意要在#后面加上**空格**
```
例如:
    # 一级标题
    ## 二级标题
    ### 三级标题
```
效果如下:
># 一级标题
>## 二级标题
>### 三级标题
<BR>
<BR>
<BR>
<BR>
<BR> 

***
## <a id="2">2.引用区块</a>  
Markdown 的引用,使用 > ：`> 文本`  
注意退出引用时要换行

    例如：

    >_panache:_  
    >仰天大笑出门去  
    >归来倚仗自叹息

效果如下：
>_panache:_  
>仰天大笑出门去  
>归来倚仗自叹息 

<BR>
<BR>
<BR>
<BR>
<BR> 

***
## <a id="3">3.代码块</a>
1. 用在代码前加入Tab键或者四个空格  
2. 用反引号\`包围代码  `(注意不是单引号'，而是Esc下与~同块的)`   
>单行用一个`就行，多行用```

3. 三个~好像也行 
```
例如:    
    '''

    #include<stdio.h>
    int main(){
        printf("Hello World");
    }


    '''
```
<BR>
<BR>
<BR>
<BR>
<BR> 

***

## <a id="4">4.注释</a>
Markdown 的注释用：
1. `<!--这是注释-->`
2. `[anything]:#(注释文本)`
3. `[anything]:<> (注释文本)`（注意<>后面有个空格）
```  
例如：
     1. <!--这是注释hhh-->
     2. [ddddd]:#(注释文本aaa)
     3. [sgsg]:<> (注释文本ddd)  
```
效果如下：
>1. <!--这是注释hhh-->   
>2. [ddddd]:#(注释文本aaa)  
>3. [sgsg]:<> (注释文本ddd) 

<BR>
<BR>
<BR>
<BR>
<BR> 
<hr>

## <a id="5">5.字体、颜色和字号</a>
```
<font face="宋体" color="green" size="3">
字体:face  
颜色:color  
字号:size
</font>
```
>效果如下:
><font face="宋体" color="green" size="3">  
>    字体:face  
>    颜色:color  
>    字号:size
></font>

<BR>
<BR>
<BR>
<BR>
<BR> 

<hr>

## <a id="6">6.斜体和加粗</a>
用<font color=green>*</font>或者<font color=green>_</font>（一个为斜体，两个为加粗）

    *文本* or _文本_
    **文本** or __文本__
>效果如下:  
>*文本* or _文本_\
>**文本** or __文本__

<BR>
<BR>
<BR>
<BR>
<BR> 
<hr>

## <a id="7">7.换行</a>
1. 用两个空格换行
2. 用`\`换行
3. 用HTML标签` <br>` 换行

<BR>
<BR>
<BR>
<BR>
<BR> 

***
## <a id="8">8.分割线</a>
1. 用`<hr>`
2. 用三个及以上`*`：`***`
3. 用三个及以上`-`：`---`
4. 用三个及以上`_`：`___`
>效果如下:
><hr>

<BR>
<BR>
<BR>
<BR>
<BR> 

***

## <a id="9">9.删除</a>
用~~(两个`~`)把文本包围
```
~~文本~~
```

>效果如下:
>~~文本~~  
>*`PS：三个~（~~~）进入代码块`*

<BR>
<BR>
<BR>
<BR>
<BR> 

***

## <a id="10">10.首行缩进</a>
1.半角空格(英) `&nbsp;`或者`&#160;`  
2.半方大的空白 `&ensp;`或者`&#8194;`  
3.全方大的空白 `&emsp;`或者`&#8195;`  
>效果如下(不要漏掉`;`):  
>&nbsp;文本1  
>&ensp;文本2  
>&emsp;文本3

<BR>
<BR>
<BR>
<BR>
<BR> 

---
## <a id="11">11.表格</a>
Markdown中用`|`来做表格:<BR>
+ 其中表头默认居中对齐，内容左对齐。  
+ 可以更改内容对齐方式：左对齐`:-`  ，居中对齐：`:-:`,右对齐：`-:` 。  
+ 两边的`|`可以舍去，不影响。
```
例如：

|表头1 |表头2 |表头3|
|:----:|:----:|:----:|
|  A   |   B  |  C   |
|  a   |   b  |  c   |

```
效果如下：
|表头1 |表头2 |表头3|
|:----:|:----:|:----:|
|  A   |   B  |  C   |
|  a   |   b  |  c   |

<BR>
<BR>
<BR>
<BR>
<BR> 

---
## <a id="12">12.序列</a>
+  有序列表用数字（1.，2.，3.，……），并在正文前空格  
+ 无序列表用（* -  +）
```
    1. 赵
    2. 钱
    3. 孙

    + 赵 
    - 钱
    * 孙
```
效果如下：
>1. 赵
>2. 钱
>3. 孙
>+ 赵
>- 钱
>* 孙


<BR>
<BR>
<BR>
<BR>
<BR> 

---
## <a id="13">13.超链接</a>
形成链接方式：  
1.`[链接名称](地址)`  
2.`<链接地址>`

    例如：
    [菜鸟教程](https://www.runoob.com/)
    <https://www.runoob.com/>

效果如下：
>[菜鸟教程](https://www.runoob.com/)  
><https://www.runoob.com/>


<BR>
<BR>
<BR>
<BR>
<BR> 

---

## <a id="14">14.图片</a>
>基本格式：`![图片属性](地址 "标题")`   
>(图片属性只有图片不能加载时替换图片作用，标题是当鼠标指向图片时才浮现，地址支持相对和绝对网地址)  
 
     例如：
     ![RUNOOB图标](http://static.runoob.com/images/runoob-logo.png "runoob")
     ![图片](xpic10582.JPG "这是一张图片的标题")

效果如下：

![RUNOOB图标](http://static.runoob.com/images/runoob-logo.png "runoob")

![图片](xpic10582.JPG "这是一张图片的标题")
<br>
<br>
<br>
* >也可以用HTML的`<img>`标签（可以更改图片大小,居中对齐）
```
例如：
<center>
<img src="http://pic22.nipic.com/20120626/8002769_150042384347_2.jpg" width=400 title="鹊桥">
</center>
```
效果如下：

<center>
<img src="http://pic22.nipic.com/20120626/8002769_150042384347_2.jpg" width=400 title="鹊桥">
</center>
<br>
<br>

>上面两种方式都要依靠图片源，似乎有方法还可以把图片整理到markdown文档。此处附[链接](https://www.jianshu.com/p/280c6a6f2594)

<BR>
<BR>
<BR>
<BR>
<BR> 

---
## <a id="15">15.图片链接</a>
有图片有链接，自然而然想到图片链接。（其实就链接+图片，把超链接中的**链接名称**用图片替代即可）
>格式：`[![atl tex](link of image)](link)`

    例如：
    &emsp;&emsp;&emsp;&emsp;&emsp;[<img src="http://pic39.nipic.com/20140330/5565441_180114054000_2.jpg" width=150 title="点击跳转到B站">](https://www.bilibili.com/)&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; [![runoob](http://static.runoob.com/images/runoob-logo.png "点击跳转到菜鸟教程")](https://www.runoob.com/)

效果如下：

&emsp;&emsp;&emsp;&emsp;&emsp;[<img src="http://pic39.nipic.com/20140330/5565441_180114054000_2.jpg" width=150 title="点击跳转到B站">](https://www.bilibili.com/)&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; [![runoob](http://static.runoob.com/images/runoob-logo.png "点击跳转到菜鸟教程")](https://www.runoob.com/)

<BR>
<BR>
<BR>
<BR>
<BR> 


***
## <a id="16">16.公式</a>
<script type="text/javascript" src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=default"></script>

1. 用\\(Latex\\)公式 
>([此方法来自-->这个大佬](https://blog.csdn.net/xiahouzuoxin/article/details/26478179)) 但其他的两个方法没有试成功,此处仅提供本人亲测有效的方法.

先添加\\(MathJax\\)引擎
>`<script type="text/javascript" src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=default"></script>`

再用latex语法写公式([详细见大佬](https://blog.csdn.net/beta_2187/article/details/79980281))
>单行用: `\\(公式\\)`  
>多行用: `$$公式$$` (公式会提行并居中)
```
<script type="text/javascript" src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=default"></script>

\\(x=\frac{-b\pm\sqrt{b^2-4ac}}{2a}\\)  

$$ x=\frac{-b\pm\sqrt{b^2-4ac}}{2a} $$

\begin{equation}\label{...}
\int_0^1f(t)dt = \iint_Dg(x,y)dxdy.
\end{equation}
```
效果如下:
><script type="text/javascript" src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=default"></script>
>
>\\(x=\frac{-b\pm\sqrt{b^2-4ac}}{2a}\\)  

>$$ x=\frac{-b\pm\sqrt{b^2-4ac}}{2a} $$

>\begin{equation}\label{...}
>\int_0^1f(t)dt = \iint_Dg(x,y)dxdy.
>\end{equation}

以下一些提供的参考可供查询:
+ [Markdown数学符号&公式](https://blog.csdn.net/katherine_hsr/article/details/79179622)
+ [Markdown中数学公式整理](https://blog.csdn.net/zdk930519/article/details/54137476)
+ [Latex数学公式表](https://blog.csdn.net/u011826404/article/details/70215074)
+ [LaTeX数学公式](https://www.cnblogs.com/wzjhoutai/p/7204404.html)
+ [常用数学符号的 LaTeX 表示方法](http://mohu.org/info/symbols/symbols.htm)


<BR>
<BR>
<BR>
<BR>
<BR> 

---
## <a id="17">17.锚点</a>
+ 详见-->[markdown如何实现锚点功能](https://blog.csdn.net/weixin_45844049/article/details/103866977)
1. 法一
>`<a href="#label">名称</a>`  
>`<a id="label">名称</a>`

2. 法二
>`[名称](#label)`  
>`<a id="label">名称</a>`




<BR>
<BR>
<BR>
<BR>
<BR> 

# 参考
[1]<https://blog.csdn.net/xiahouzuoxin/article/details/26478179>
[2]<https://blog.csdn.net/beta_2187/article/details/79980281>
[3]<https://blog.csdn.net/weixin_45844049/article/details/103866977>
[4]<https://www.jianshu.com/p/280c6a6f2594>
[5]<https://blog.csdn.net/geekleee/article/details/73018194>
[6]<https://www.jianshu.com/p/2df05f279331/>  
[7]<https://www.luogu.com.cn/blog/Lu-Anlai/Markdown-link-and-picture>

***
