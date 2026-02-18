# Jekyll + GitHub Pages 博客部署指南

这是一个使用 Jekyll 和 GitHub Pages 搭建的静态博客，完全免费，零配置自动部署。

## 📁 项目结构

```
gitHubPages/
├── _config.yml          # Jekyll 配置文件
├── _layouts/            # 布局模板
│   ├── default.html     # 默认布局
│   └── post.html        # 文章布局
├── _posts/              # 博客文章目录
│   ├── 2025-02-18-welcome-to-my-blog.md
│   └── 2025-02-18-jekyll-beginner-guide.md
├── about.md             # 关于页面
├── index.html           # 首页
├── Gemfile              # Ruby 依赖管理
└── .gitignore           # Git 忽略文件
```

## 🚀 快速开始

### 1. 本地预览（可选）

如果你想本地预览博客效果，需要先安装 Ruby 和 Bundler：

#### Windows 安装 Ruby

1. 下载并安装 RubyInstaller: https://rubyinstaller.org/
2. 安装时勾选 "Add Ruby executables to your PATH"
3. 打开终端，运行：
   ```bash
   gem install bundler
   ```

#### 安装依赖并启动本地服务器

```bash
# 进入项目目录
cd g:\Codes\MagicCalculator\gitHubPages

# 安装依赖
bundle install

# 启动本地服务器
bundle exec jekyll serve
```

访问 http://localhost:4000 即可预览博客。

### 2. 部署到 GitHub Pages

#### 步骤 1：创建 GitHub 仓库

1. 登录 GitHub，创建新仓库
2. 仓库名称必须为：`你的用户名.github.io`
   - 例如：如果你的用户名是 `zhangsan`，仓库名就是 `zhangsan.github.io`
3. 选择 Public（公开仓库）

#### 步骤 2：配置 `_config.yml`

打开 `_config.yml` 文件，修改以下内容：

```yaml
title: 你的博客标题
email: your-email@example.com
description: >
  你的博客描述
baseurl: ""
url: "https://你的用户名.github.io"
```

#### 步骤 3：推送到 GitHub

```bash
# 初始化 Git 仓库
git init

# 添加所有文件
git add .

# 提交
git commit -m "Initial commit"

# 添加远程仓库（替换为你的仓库地址）
git remote add origin https://github.com/你的用户名/你的用户名.github.io.git

# 推送到 GitHub
git push -u origin main
```

#### 步骤 4：等待部署

推送成功后，GitHub 会自动构建你的博客。通常需要 1-3 分钟。

访问 `https://你的用户名.github.io` 即可看到你的博客！

## ✍️ 写作指南

### 创建新文章

在 `_posts` 目录下创建新的 Markdown 文件，文件名格式：`YYYY-MM-DD-标题.md`

例如：`2025-02-18-my-new-post.md`

### 文章 Front Matter

每个文章文件开头必须包含 Front Matter：

```yaml
---
layout: post
title: 文章标题
date: 2025-02-18 10:00:00 +0800
categories: 技术
---

文章内容...
```

### Markdown 语法示例

```markdown
# 一级标题
## 二级标题
### 三级标题

**粗体文本**
*斜体文本*

- 无序列表项 1
- 无序列表项 2

1. 有序列表项 1
2. 有序列表项 2

[链接文本](https://example.com)

![图片描述](image.jpg)

```python
代码块
```

> 引用文本
```

## 🎨 自定义样式

所有样式都在 `_layouts/default.html` 的 `<style>` 标签中。你可以根据需要修改：

- 颜色主题
- 字体
- 间距
- 布局

## 📝 常用命令

```bash
# 安装依赖
bundle install

# 启动本地服务器
bundle exec jekyll serve

# 构建网站
bundle exec jekyll build

# 查看帮助
bundle exec jekyll help
```

## 🔧 配置说明

### `_config.yml` 主要配置项

```yaml
title: 网站标题
email: 你的邮箱
description: 网站描述
baseurl: 子目录路径（如果有）
url: 网站完整 URL
permalink: 文章链接格式

plugins:
  - jekyll-sitemap    # 生成网站地图
  - jekyll-feed       # 生成 RSS 订阅
```

## 🌐 自定义域名（可选）

如果你有自己的域名，可以这样配置：

1. 在项目根目录创建 `CNAME` 文件
2. 文件内容写你的域名，例如：`www.yourdomain.com`
3. 在域名提供商处添加 DNS 记录：
   - A 记录：`185.199.108.153`、`185.199.109.153`、`185.199.110.153`、`185.199.111.153`
   - 或 CNAME 记录：`你的用户名.github.io`

## 📚 更多资源

- [Jekyll 官方文档](https://jekyllrb.com/docs/)
- [GitHub Pages 文档](https://docs.github.com/pages)
- [Liquid 模板语言](https://shopify.github.io/liquid/)
- [Markdown 语法](https://www.markdownguide.org/)

## ❓ 常见问题

### Q: 本地预览正常，但 GitHub 上显示 404？

A: 检查以下几点：
1. 仓库名称是否正确（必须是 `用户名.github.io`）
2. `_config.yml` 中的 `url` 是否正确
3. 等待几分钟，GitHub 需要时间构建
4. 检查仓库设置中的 GitHub Pages 是否启用

### Q: 如何修改主题？

A: 你可以：
1. 自己修改 CSS 样式（在 `_layouts/default.html` 中）
2. 使用 Jekyll 主题（在 `_config.yml` 中添加 `theme: 主题名`）

### Q: 如何添加图片？

A: 将图片放在项目根目录或 `images` 文件夹中，然后在 Markdown 中引用：
```markdown
![图片描述](/images/your-image.jpg)
```

### Q: 如何添加评论功能？

A: 可以集成第三方评论系统，如：
- [Gitalk](https://gitalk.github.io/)
- [Giscus](https://giscus.app/)
- [Disqus](https://disqus.com/)

## 🎉 开始写作吧！

现在你已经拥有了一个完全免费的博客，开始记录你的想法和分享你的知识吧！

记住：**选择框架只需要 5 分钟，写好内容需要一辈子。** 不要过度纠结技术细节，专注于创作优质内容才是最重要的！
