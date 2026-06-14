# Empty Homepage + Blog Starter

这是一个空的 Jekyll 静态博客骨架，结构参考当前仓库的主页 + 博客模式，但把个人信息、文章、图片、评论和统计都留成占位。

## 你主要需要填写哪里

- `_config.yml`：站点名称、作者信息、导航、社交链接、网址。
- `index.html`：主页内容。
- `about/index.md`：关于页。
- `_posts/`：正式发布的文章。
- `_drafts/example-post.md`：文章草稿模板，可以复制到 `_posts/`。
- `assets/images/profile-placeholder.svg`：替换成你的头像或主页图片。

完整中文操作说明见：

```text
HOW_TO_USE.md
```

## 写新文章

文章文件名必须放在 `_posts/`，格式为：

```text
yyyy-mm-dd-title.md
```

例如：

```text
2026-06-14-my-first-post.md
```

文章头部示例：

```yaml
---
layout: post
title: "文章标题"
date: 2026-06-14
tags: [Coding, Notes]
excerpt: "一句话摘要。"
---
```

## 本地预览

推荐使用 Ruby 3.1 来跑 GitHub Pages / Jekyll。本机如果是 macOS + Homebrew，可以这样配置：

```bash
brew install ruby@3.1
echo 'export PATH="/opt/homebrew/opt/ruby@3.1/bin:/opt/homebrew/lib/ruby/gems/3.1.0/bin:$PATH"' >> ~/.zshrc
source ~/.zshrc
```

然后进入项目目录：

```bash
bundle install
bundle exec jekyll serve
```

然后打开：

```text
http://127.0.0.1:4000
```

## GitHub Pages

如果你创建的是用户主页仓库，例如 `yourname.github.io`：

```yaml
url: "https://yourname.github.io"
baseurl: ""
```

如果你创建的是项目页仓库，例如 `my-blog`：

```yaml
url: "https://yourname.github.io"
baseurl: "/my-blog"
```
