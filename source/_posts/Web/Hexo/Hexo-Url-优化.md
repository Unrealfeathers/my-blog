---
title: Hexo Url 优化
math: false
mermaid: false
permalink: /posts/20250403-102534.html
date: 2025-04-03 10:25:34
tags:
  - Hexo
  - Fluid
categories:
  - 教程 
---
## Hexo Url 优化
进入`_config.fluid.yml`中，修改如下：

<!-- more -->

```yml
# URL
url: https://flowerdown.org
root: /
permalink: :permalink
permalink_defaults:
pretty_urls:
  trailing_index: true # Set to false to remove trailing 'index.html' from permalinksjin
  trailing_html: true  # Set to false to remove trailing '.html' from permalinks
```
这个时候，文章的 Url 链接会默认使用文章开头 [front-matter](https://hexo.io/zh-cn/docs/front-matter)中配置 的`permalink: /posts/example.html` 属性。如果不喜欢文章 Url 末尾的`.html`，则可以修改`trailing_index`和`trailing_html`属性，但是文章中的`permalink`也要一起修改。