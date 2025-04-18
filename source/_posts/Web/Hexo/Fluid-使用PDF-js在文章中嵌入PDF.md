---
title: Fluid 使用PDF.js在文章中嵌入PDF
math: false
mermaid: false
permalink: /posts/20250404-135907.html
date: 2025-04-04 13:59:07
tags:
  - Hexo
  - Fluid
  - PDF.js
categories:
  - 教程 
---
## PDF.js
进入[PDF.js的官网](https://mozilla.github.io/pdf.js/getting_started/#download)下载压缩包，将其解压后重命名文件夹为`pdfjs`。  

<!-- more -->

## 配置Fluid
1. 在根目录的`source`目录下，新建`js`文件夹，将`pdfjs`放入`js`文件夹。  
2. 然后同样在`source`目录下，新建`pdf`文件夹，用于放入你的pdf文件。
3. 修改配置文件`_config.fluid.yml`，搜索`skip_render`，修改为`skip_render: [js/pdfjs/**]`

## 文章中添加PDF
```html
<div>
	<iframe src="/js/pdfjs/web/viewer.html?file=/pdf/example.pdf" width="100%" height="800px"></iframe>
</div>
```

## 效果如下

<div>
	<iframe src="/js/pdfjs/web/viewer.html?file=/pdf/微积分公式大全.pdf" width="100%" height="800px"></iframe>
</div>
