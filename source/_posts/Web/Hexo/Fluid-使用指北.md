---
title: Fluid 使用指北
math: false
mermaid: false
permalink: /posts/20250401-203748.html
date: 2025-04-01 20:37:48
tags: 
  - Hexo
  - Fluid
  - Markdown
categories:
  - 教程 
---
## 首页
> * [配置指南 | Hexo Fluid 用户手册](https://hexo.fluid-dev.com/docs/guide)  

<!-- more -->

### 摘要
手动在正文中添加`<!-- more -->`，标识符前面的内容作为摘要。在  [front-matter](https://hexo.io/zh-cn/docs/front-matter)里设置  `excerpt` 字段，如：  
```yaml
---
title: 这是标题
excerpt: 这是摘要
---
```
> * TIP  
> * 优先级: 手动摘要 > 自动摘要  
> * 如果关闭自动摘要，并且没有设置手动摘要，摘要区域空白  
> * 无论哪种摘要都最多显示 3 行，当屏幕宽度不足时会隐藏部分摘要  

### 隐藏文章
如果想把某些文章隐藏，**不在首页和其他归档分类页里展示**，可以在文章开头 [front-matter](https://hexo.io/zh-cn/docs/front-matter)中配置 `hide: true` 属性。

### 归档文章
如果只是想让文章在首页隐藏，但仍**需要在归档分类页里展示**，可以在文章开头 [front-matter](https://hexo.io/zh-cn/docs/front-matter)中配置 `archive: true` 属性。

### 文章排序
如果想手动将某些文章固定在首页靠前的位置，可以在安装 `hexo-generator-index` >= 2.0.0 版本的情况下，在文章开头 [front-matter](https://hexo.io/zh-cn/docs/front-matter)中配置 `sticky` 属性。`sticky` 数值越大，该文章越靠前，达到类似于置顶的效果，其他未设置的文章依然按默认排序。当文章设置了 `sticky` 后，主题会默认在首页文章标题前增加一个图标，来标识这是一个置顶文章，你可以通过**主题配置**去关闭或修改这个功能。

## 文章页
### 文章在首页的封面图
在文章开头 [front-matter](https://hexo.io/zh-cn/docs/front-matter)中配置 `index_img` 属性，可使用本地图片或者外部链接。
```yaml
index_img: /img/example.jpg
index_img: https://example.com/example.jpg
```

### 文章页顶部大图
默认显示**主题配置**中的 `post.banner_img`，如需要设置单个文章的 Banner，在 [front-matter](https://hexo.io/zh-cn/docs/front-matter)中指定 `banner_img` 属性。
```yaml
banner_img: /img/example.jpg
banner_img: https://example.com/example.jpg
```

### 文章内容图片
```md
![](/img/example.jpg)
```

### 脚注
```md
正文
引用[^1]

## 参考
[^1]: 参考资料1
```

### 便签
在 markdown 中加入如下的代码来使用便签：
```md
{% note success %}
文字 或者 `markdown` 均可
{% endnote %}
```
> * WARNING  
> * 使用时 `{% note primary %}` 和 `{% endnote %}` 需单独一行，否则会出现问题

可选便签：

| 名称        | 颜色  |
| --------- | --- |
| primary   | 紫色  |
| secondary | 灰色  |
| success   | 绿色  |
| danger    | 红色  |
| warning   | 黄色  |
| info      | 蓝色  |
| light     | 黑色  

### 行内标签
在 markdown 中加入如下的代码来使用 Label：
```md
{% label primary @text %}
```

可选 Label：

| 名称      | 颜色  |
| ------- | --- |
| primary | 紫色  |
| default | 灰色  |
| success | 绿色  |
| danger  | 红色  |
| warning | 黄色  |
| info    | 蓝色  |

### 折叠块
使用折叠块，可以折叠代码、图片、文字等任何内容，你可以在 markdown 中按如下格式，颜色同上：
```md
{% fold info @title %}
需要折叠的一段内容，支持 markdown
{% endfold %}
```
> * info: 和行内标签类似的可选参数  
> * title: 折叠块上的标题  

### 勾选框
在 markdown 中加入如下的代码来使用 Checkbox：
```md
{% cb text, checked?, incline? %}
```
> * text：显示的文字  
> * checked：默认是否已勾选，默认 false  
> * incline: 是否内联（可以理解为后面的文字是否换行），默认 false  

### 按钮
在 markdown 中加入如下的代码来使用 Button：
```md
{% btn url, text, title %}
```
> * url：跳转链接  
> * text：显示的文字  
> * title：鼠标悬停时显示的文字（可选）  

### 组图
如果想把多张图片按一定布局组合显示，你可以在 markdown 中按如下格式：
```md
{% gi total n1-n2-... %}
  ![](url)
  ![](url)
  ![](url)
  ![](url)
  ![](url)
{% endgi %}
```
> * total：图片总数量，对应中间包含的图片 url 数量  
> * n1-n2-...：每行的图片数量，可以省略，默认单行最多 3 张图，求和必须相等于 total，否则按默认样式

## LaTeX 数学公式
> * [LaTeX](https://www.latex-project.org/help/documentation/)

只有在文章 [front-matter](https://hexo.io/zh-cn/docs/front-matter)里指定 `math: true` 才会在文章页启动公式转换，以便在页面不包含公式时提高加载速度。
```md
$$
E=mc^2
$$
```

### Mermaid 流程图
> * [Mermaid](http://mermaid-js.github.io/mermaid/#/)

只有在文章 [front-matter](https://hexo.io/zh-cn/docs/front-matter)里指定 `mermaid: true` 才会在文章页启动流程图渲染，以便在页面不包含流程图时提高加载速度。
使用 Mermaid 可以通过内置的 Tag 书写：
```md
{% mermaid %}
gantt
dateFormat  YYYY-MM-DD
title Adding GANTT diagram to mermaid

section A section
Completed task            :done,    des1, 2014-01-06,2014-01-08
Active task               :active,  des2, 2014-01-09, 3d
Future task               :         des3, after des2, 5d
Future task2               :         des4, after des3, 5d
{% endmermaid %}
```
也可以通过代码块书写：
````md
```mermaid
classDiagram
Class01 <|-- AveryLongClass : Cool
Class03 *-- Class04
Class05 o-- Class06
Class07 .. Class08
Class09 --> C2 : Where am i?
Class09 --* C3
Class09 --|> Class07
Class07 : equals()
Class07 : Object[] elementData
Class01 : size()
Class01 : int chimp
Class01 : int gorilla
Class08 <--> C2: Cool label
````