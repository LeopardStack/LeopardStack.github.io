# Leopard Notes

科技与人文的交汇处 —— 基于 [Hugo](https://gohugo.io/) + [PaperMod](https://github.com/adityatelange/hugo-PaperMod) 的个人博客。

## 项目结构

```
├── hugo.yaml                    # 站点配置
├── archetypes/
│   └── posts.md                 # 新文章 front matter 模板
├── content/
│   ├── archives.md              # 归档页
│   ├── search.md                # 搜索页
│   ├── about/index.md           # 关于页
│   └── posts/
│       ├── tech/                # 技术文章（每篇一个目录，图片放各自 images/ 下）
│       └── humanities/          # 人文文章
├── layouts/shortcodes/
│   └── bilibili.html            # B 站视频嵌入 shortcode
├── static/images/               # 全局图片（头像、logo 等）
├── themes/PaperMod/             # 主题（git submodule）
└── .github/workflows/deploy.yml # GitHub Actions 自动部署
```

## 本地运行

```bash
# 克隆（注意 --recursive 拉取主题 submodule）
git clone --recursive https://github.com/LeopardStack/LeopardStack.github.io.git

# 本地预览（含草稿），访问 http://localhost:1313
hugo server -D

# 构建（输出到 public/）
hugo --gc --minify
```

## 写文章

```bash
# 新建文章（page bundle 形式，图片放同目录 images/ 下）
hugo new posts/tech/my-post/index.md          # 技术文章
hugo new posts/humanities/my-essay/index.md   # 人文随笔
```

写完后把 front matter 中的 `draft: true` 改为 `false`。

- 分类：`categories: ["tech"]` 或 `["humanities"]`（对应导航菜单）
- 本地图片：`![描述](images/xxx.png)`
- B 站视频：`{{</* bilibili BV号 */>}}`
- YouTube：`{{</* youtube 视频ID */>}}`

## 部署

push 到 `main` 分支后，GitHub Actions 自动构建并发布到 GitHub Pages。

首次部署需在仓库 **Settings → Pages** 中把 **Source** 设为 **GitHub Actions**。

## 更新主题

```bash
git submodule update --remote --merge themes/PaperMod
```
