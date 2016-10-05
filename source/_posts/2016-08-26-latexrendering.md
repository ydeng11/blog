---
title: Hexo渲染LaTex公式的问题
date: 2016-08-26 15:08:46
tags:
 - Markdown
categories: 网页编辑
---

> 好事多磨

在使用Hexo搭建静态博客后，写文章非常的爽利，用Markdown写完后直接交个Hexo渲染就好了。但是在对公式的支持上却有一点点不如人意的地方。虽然Next主题在最新的版本已经支持MathJax，方便了我们使用LaTex来编写公式。<!---more--->Hexo的渲染机制却会与Markdown相冲突，导致网页显示不正常或不能显示。

最主要的问题就是下划线"_"的使用，在hexo里下划线会先被渲染成斜体或加强体，因此MathJax就无法准确渲染我们编写的公式。在这里，我搜索到了三个方法。

 1. 对下划线"_"加"\"进行转义，但是在Markdown编辑器就无法实时预览了。我的解决办法是先编写好再加转义符。
 2. 在公式的上下使用"{%raw%}"和"{%endraw%}"，这样可以停止对特殊字符的渲染。
 3. 使用Pandoc-Markdown编辑器，hexo-render-pandoc。 
 4. 对Hexo的脚本文件进行修改。（不推荐）
> hexo\node_modules\marked\lib\marked.js


修改第449行

    escape: /^\\([\\`*{}\[\]()#+\-.!_>])/,

为

    escape:/^\\([`*\[\]()#+\-.!_>])/,

修改第847行

    return '<em>' + text +'</em>'

为

    return '_' + text + '_';


