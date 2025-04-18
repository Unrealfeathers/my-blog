---
title: Fluid 修改404页面
math: false
mermaid: false
permalink: /posts/20250402-141231.html
date: 2025-04-02 14:12:31
tags:
  - Hexo
  - Fluid
categories:
  - 教程 
---
## Fluid 修改404页面
我们可以在`node_modules\hexo-theme-fluid\layout\404.ejs`找到 Fluid 的官方layout。  

<!-- more -->

```js
<%
page.layout = "404"
page.title = theme.page404.title || __('page404.title')
page.subtitle = theme.page404.subtitle || __('page404.subtitle')
page.banner_img = theme.page404.banner_img
page.banner_img_height = theme.page404.banner_img_height
page.banner_mask_alpha = theme.page404.banner_mask_alpha
%>

<script>
	function redirect() {
		location.href = "<%- url_for('/') %>";
	}
	<% if (theme.page404.redirect_delay) { %>
		setTimeout(redirect, <%= parseInt(theme.page404.redirect_delay) %>)
	<% } %>
</script>
```

根据文件，我们可以看出来404页面是在`_config.fluid.yml`中的page404字段下配置,例如：  
```yml
# 404页
page404:
	banner_img: https://example.com/example.jpg
	banner_img_height: 100%
	banner_mask_alpha: 0.05
```