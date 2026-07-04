# 项目说明（AI 助手请先读我）

这是一个 Hugo + PaperMod 的中文个人博客（科技人文主题），部署在 GitHub Pages，
push 到 main 分支即自动发布。

## 目录规范

- 技术文章：`content/posts/tech/<英文或拼音目录名>/index.md`
- 人文随笔：`content/posts/humanities/<英文或拼音目录名>/index.md`
- 系列连载：给系列建子目录，按序号命名各篇，如
  `content/posts/tech/jdk21-spring/01-jdk21-features/index.md`、`02-spring-version/`……
  每篇 front matter 加 `series: ["系列名"]`（同系列必须一字不差），
  Hugo 自动生成 `/series/<系列名>/` 聚合页；标题带序号如「系列名（一）：……」
- 每篇文章是一个 page bundle：图片放文章同级的 `images/` 目录，正文用 `![描述](images/xxx.png)` 引用
- 全局图片（头像、logo）放 `static/images/`
- 不要修改 `themes/PaperMod/`（git submodule）和 `public/`（构建产物）

## 文章 front matter 规范

```yaml
---
title: "文章标题"
date: 2026-07-05T10:00:00+08:00   # 东八区，不能是未来时间（否则不显示）
draft: true                        # 新文章一律先设 true，作者确认后才改 false
summary: "一句话摘要，显示在列表页"
categories: ["tech"]               # 只能是 tech 或 humanities（新栏目需先改 hugo.yaml 菜单）
tags: ["标签1", "标签2"]
series: ["系列名"]                 # 仅系列连载文章需要；单篇文章省略此字段
cover:                             # 可选
  image: "images/cover.png"
  relative: true                   # page bundle 内必须为 true
---
```

## 视频嵌入短代码

- B 站：`{{</* bilibili BV号 */>}}`（自定义 shortcode，见 layouts/shortcodes/bilibili.html）
- YouTube：`{{</* youtube 视频ID */>}}`

## 图表（图文并茂优先用这个）

- 流程图/架构图/时序图直接写 ```mermaid 代码块，站点自动渲染
  （render hook 见 layouts/_markup/render-codeblock-mermaid.html，脚本按需自动注入）
- 需要截图/照片/示意图时用文字占位「（图：xxx）」，不要生成假图片

## 写作约定

- 语言：简体中文；代码、专有名词保留英文
- 技术文章：讲清楚"为什么"再讲"怎么做"，代码块必须标注语言以启用高亮，
  关键步骤给出可运行的完整示例，不编造 API 和版本号，不确定的内容要标注存疑
- 人文随笔：散文风格，克制使用小标题和列表，不写空话套话
- 引用外部图片/数据需注明来源

## 双语

- 站点双语：中文（默认，/）+ 英文（/en/）。给文章出英文版 = 在同一文件夹加 index.en.md，
  图片共用 images/；未翻译的文章只出现在中文站，这是正常现象
- 英文版 front matter 结构与中文版一致（title/summary/tags 用英文），date 保持相同

## 评论

- giscus（GitHub Discussions），配置在 hugo.yaml params.giscus；单篇关闭评论用 comments: false

## 验证与发布

- 写完后运行 `hugo`（或 `hugo server -D` 预览）确认构建无 ERROR
- 未经作者明确要求，不要执行 `git push`；commit 信息格式：`post: 文章标题` / `docs: ...` / `chore: ...`
