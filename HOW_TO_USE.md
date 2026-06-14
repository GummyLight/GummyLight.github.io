# 使用指南：主页、博客、GitHub Pages 部署

这份模板是一个 Jekyll 静态站点。你只需要写 Markdown / HTML，Jekyll 会把它们生成网页，GitHub Pages 会负责在线部署。

## 1. 怎么写主页

主页由两个地方共同控制：

- `_config.yml`：站点和个人信息。
- `index.html`：主页版面和正文内容。

### 第一步：先改站点信息

打开 `_config.yml`，优先修改这些字段：

```yaml
title: "你的名字"
tagline: "Personal Homepage and Blog"
description: "一句话介绍这个网站。"
lang: "zh-CN"

author:
  name: "你的名字"
  role: "你的身份 / 研究方向 / 工作方向"
  bio: "一两句话介绍你正在做什么。"
  email: "you@example.com"
  avatar: "/assets/images/profile-placeholder.svg"
```

如果你有自己的头像或主页图，放到 `assets/images/`，例如：

```text
assets/images/me.jpg
```

然后把 `_config.yml` 里的头像路径改成：

```yaml
avatar: "/assets/images/me.jpg"
```

### 第二步：改主页内容

打开 `index.html`。主页当前分三块：

- 顶部个人介绍：自动读取 `_config.yml` 里的 `author` 信息。
- `What I am working on`：填写你现在的方向、项目、研究、近况。
- `Recent posts`：自动显示最近 3 篇博客，不需要手动维护。

你主要改这一段：

```html
<section class="section">
  <div class="section__header">
    <p class="eyebrow">Now</p>
    <h2>What I am working on</h2>
  </div>
  <div class="plain-list">
    <p>Replace this paragraph with your current research direction, notes, or life updates.</p>
  </div>
</section>
```

可以改成：

```html
<section class="section">
  <div class="section__header">
    <p class="eyebrow">Now</p>
    <h2>Research Notes</h2>
  </div>
  <div class="plain-list">
    <p>我目前关注机器人感知、SLAM、具身智能导航，以及相关论文阅读和工程复现。</p>
  </div>
</section>
```

### 第三步：改关于页

打开：

```text
about/index.md
```

这里适合写更完整的个人介绍，例如：

- 教育经历
- 研究方向
- 项目经历
- 论文 / 专利 / 作品链接
- 联系方式

### 第四步：改导航栏

导航栏在 `_config.yml`：

```yaml
navigation:
  - name: "Home"
    url: "/"
  - name: "Blog"
    url: "/blog/"
  - name: "Archive"
    url: "/archive/"
  - name: "About"
    url: "/about/"
```

如果暂时不想显示某个入口，直接删掉对应两行即可。

## 2. 怎么发布博客

正式文章都放在：

```text
_posts/
```

Jekyll 要求文章文件名使用这个格式：

```text
YYYY-MM-DD-title.md
```

例如：

```text
2026-06-14-my-first-post.md
2026-06-15-robotics-reading-notes.md
2026-06-16-slam-system-review.md
```

### 推荐命名格式

为了长期维护整齐，建议统一成：

```text
YYYY-MM-DD-category-short-title.md
```

例子：

```text
2026-06-14-note-how-to-build-blog.md
2026-06-15-paper-intent-mpc.md
2026-06-16-code-jekyll-setup.md
2026-06-17-life-reading-list.md
```

可以使用这些分类前缀：

```text
note-   普通笔记
paper-  论文阅读
code-   编程/配置/工程
exp-    实验记录
life-   生活/阅读/随笔
proj-   项目总结
```

文件名建议只用小写英文、数字和连字符：

```text
good: 2026-06-14-paper-intent-mpc.md
bad:  2026-06-14-论文阅读 Intent MPC.md
```

中文标题可以写在文章头部的 `title` 里，不建议写进文件名。

### 文章模板

可以复制这个文件：

```text
_drafts/example-post.md
```

复制到 `_posts/` 后，改成正式文件名。文章开头必须有 YAML 头信息：

```yaml
---
layout: post
title: "这里写中文标题"
date: 2026-06-14
tags: [Notes, Coding]
excerpt: "这里写一句话摘要。"
---
```

下面就是正文：

```markdown
## 引言

这里开始写正文。

## 小节标题

- 要点一
- 要点二
```

### 草稿怎么写

草稿可以先放在：

```text
_drafts/
```

例如：

```text
_drafts/paper-intent-mpc.md
```

草稿不会被正式发布。写完后复制到 `_posts/`，并改成带日期的文件名。

### 本地预览

进入项目目录：

```bash
cd /Users/lichangjin/00-个人事务/KwanWaiPang.github.io-main/blog-starter
bundle exec jekyll serve
```

浏览器打开：

```text
http://127.0.0.1:4000/
```

只要服务还在运行，修改文章或页面后刷新浏览器即可看到效果。

## 3. 怎么部署在 github.io

GitHub Pages 有两种常见部署方式。

### 方式 A：用户主页，推荐新手用

这种方式的网址是：

```text
https://你的GitHub用户名.github.io/
```

仓库名必须是：

```text
你的GitHub用户名.github.io
```

例如你的 GitHub 用户名是 `octocat`，仓库名就必须是：

```text
octocat.github.io
```

#### 操作步骤

1. 在 GitHub 新建仓库，仓库名写成 `你的用户名.github.io`。
2. 把 `blog-starter` 里面的内容复制到这个新仓库的根目录。
3. 修改 `_config.yml`：

```yaml
url: "https://你的用户名.github.io"
baseurl: ""
```

4. 提交并推送：

```bash
git add .
git commit -m "Initialize personal homepage and blog"
git push
```

5. 到 GitHub 仓库页面，进入 `Settings -> Pages`。
6. 在 `Build and deployment` 里选择：

```text
Source: Deploy from a branch
Branch: main
Folder: / (root)
```

7. 保存后等待 GitHub Pages 构建完成。

### 方式 B：项目页

这种方式的网址是：

```text
https://你的GitHub用户名.github.io/仓库名/
```

例如仓库名是 `my-blog`：

```text
https://你的GitHub用户名.github.io/my-blog/
```

这种方式适合你已经有一个主站，还想再放一个独立博客。

#### 操作步骤

1. 在 GitHub 新建普通仓库，例如 `my-blog`。
2. 把 `blog-starter` 里面的内容复制到这个仓库的根目录。
3. 修改 `_config.yml`：

```yaml
url: "https://你的用户名.github.io"
baseurl: "/my-blog"
```

4. 提交并推送。
5. 到仓库 `Settings -> Pages`。
6. 选择：

```text
Source: Deploy from a branch
Branch: main
Folder: / (root)
```

7. 保存并等待构建。

## 推送到 GitHub 的常用命令

第一次推送：

```bash
git init
git add .
git commit -m "Initialize site"
git branch -M main
git remote add origin https://github.com/你的用户名/你的仓库名.git
git push -u origin main
```

以后更新：

```bash
git add .
git commit -m "Update site"
git push
```

## 不要上传什么

这些是本地生成文件，不需要手动上传：

```text
_site/
.sass-cache/
.jekyll-cache/
.jekyll-metadata
.bundle/
vendor/bundle/
```

模板里的 `.gitignore` 已经帮你忽略它们。

## 常见问题

### 页面样式丢了

多半是 `_config.yml` 的 `baseurl` 写错了。

用户主页：

```yaml
baseurl: ""
```

项目页：

```yaml
baseurl: "/仓库名"
```

### 新文章没有出现

检查三件事：

1. 文件是否放在 `_posts/`。
2. 文件名是否是 `YYYY-MM-DD-title.md`。
3. 文章头部是否有 `layout: post`。

### GitHub Pages 没有更新

到仓库的 `Actions` 页面看构建是否失败。如果失败，点进去看红色报错。通常是 YAML 头信息格式、文件名、路径或 `_config.yml` 写错。

## 参考

- GitHub Pages Quickstart: https://docs.github.com/pages/quickstart
- GitHub Pages 发布源设置: https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site
- GitHub Pages + Jekyll 添加文章: https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/adding-content-to-your-github-pages-site-using-jekyll
