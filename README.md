# hananiahhsu.github.io

基于 GitHub Pages + Jekyll（minima 主题）的个人主页 / 博客 / 项目页。

## 本地预览（可选）
1) 安装 Ruby 与 Bundler（非必须，线上可直接构建）。
2) `bundle init && echo 'gem "github-pages", group: :jekyll_plugins' >> Gemfile`
3) `bundle install`
4) `bundle exec jekyll serve` 然后打开 http://127.0.0.1:4000

## 目录结构
- `_posts/`：Markdown 文章，文件名形如 `YYYY-MM-DD-title.md`
- `about.md`：关于页
- `projects.md`：项目页
- `blog/index.md`：博客归档页
- `assets/main.scss`：自定义样式
- `_config.yml`：站点配置

## 发布
将所有文件推送到仓库默认分支（main）。在仓库 **Settings → Pages** 选择 From Branch: `main` / 根目录 `/`。约 1 分钟后访问：

```
https://hananiahhsu.github.io
```

## 写作
新建文件 `_posts/YYYY-MM-DD-your-title.md`，添加 YAML Front Matter：

```yaml
---
layout: post
title: "你的标题"
date: 2025-10-08
categories: [category1, category2]
tags: [tag1, tag2]
---
```

然后正文用 Markdown 即可。