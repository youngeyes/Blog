# Youngeyes's Blog

## 博客搭建
此博客是用<em>github Pages</em>和<em><a href="http://jekyll.com.cn/">Jekyll</a><em>搭建的，在此特别感谢大佬<em>Ovilia's</em> <a href="https://github.com/Ovilia/blog">blog.

## 博客撰写规范
此博客的所有文章采用Markdown编写，文章中可以任意穿插html和js代码，编写规范模板如下：
## 头部yml
 `---
 title: 标题
 subtitle: 副标题	（可选）
 time: 2017.05.05
 layout: post
 tags:
 - tags1
 - tags2
 - tags3
 - ...
 series: 系列博文名	（可选）
 excerpt: 博文概要
 ---`
## 加载图片的使用
`<img class="single-img" src="{{ site.loadingImg }}" data-src="{{ site.url }}/img/post/2017-05-05.jpg">

{% capture imgSrc %}{{ site.url }}/img/post/2017-03-05.png{% endcapture %}
{% include figure.html src=imgSrc caption='图片描述文本' %}`
