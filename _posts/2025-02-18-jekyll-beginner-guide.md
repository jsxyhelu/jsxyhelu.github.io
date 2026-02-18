---
layout: post
title: Jekyll 博客入门指南
date: 2025-02-18 11:00:00 +0800
categories: 技术
---

本文将介绍 Jekyll 的基本概念和使用方法。

## 什么是 Jekyll？

Jekyll 是一个简单的、博客感知的静态网站生成器。它将纯文本转换为静态网站和博客。

## 核心概念

### Front Matter

每个 Jekyll 文件的开头都可以包含 Front Matter，用于设置页面的元数据：

```yaml
---
layout: post
title: 文章标题
date: 2025-02-18 10:00:00 +0800
categories: 技术
---
```

### Layouts

Layouts 是模板文件，定义了页面的整体结构。常用的布局包括：

- `default.html`：默认布局
- `post.html`：文章布局
- `page.html`：页面布局

### Posts

博客文章放在 `_posts` 目录下，文件名格式为 `YYYY-MM-DD-标题.md`。

### Pages

独立页面放在根目录下，如 `about.md`、`contact.md`。

## 常用变量

Jekyll 提供了许多内置变量，例如：

- `site.title`：网站标题
- `site.description`：网站描述
- `page.title`：页面标题
- `page.content`：页面内容
- `site.posts`：所有文章列表

## Liquid 模板

Jekyll 使用 Liquid 模板语言，可以轻松遍历和显示数据：

```liquid
{% for post in site.posts %}
  <h2>{{ post.title }}</h2>
  <p>{{ post.excerpt }}</p>
{% endfor %}
```

## 总结

Jekyll 是一个强大而简单的静态网站生成器，配合 GitHub Pages 可以轻松搭建个人博客。掌握这些基本概念后，你就可以开始创建自己的博客了！
