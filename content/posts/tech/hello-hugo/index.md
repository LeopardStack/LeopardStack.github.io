---
title: "用 Hugo + PaperMod 搭建个人博客"
date: 2026-07-04T10:00:00+08:00
draft: false
summary: "记录本站的搭建过程，同时演示代码高亮、本地图片、视频嵌入等常用排版。"
categories: ["tech"]
tags: ["Hugo", "博客"]
cover:
  image: "images/cover.png"
  alt: "Hugo + PaperMod"
  caption: "本站技术栈：Hugo + PaperMod"
  relative: true  # 页面包（page bundle）内的相对路径需要开启
---

## 为什么选择 Hugo

Hugo 是用 Go 编写的静态站点生成器，构建速度极快，全站秒级生成。
配合 PaperMod 主题，开箱即得暗色模式、站内搜索、归档等功能。

## 常用排版演示

### 代码块

技术文章少不了代码，PaperMod 自带行号和复制按钮：

```python
def fib(n: int) -> int:
    """返回第 n 个斐波那契数"""
    a, b = 0, 1
    for _ in range(n):
        a, b = b, a + b
    return a

print([fib(i) for i in range(10)])
```

```go
package main

import "fmt"

func main() {
    fmt.Println("Hello, Hugo!")
}
```

### 本地图片

图片直接放在文章同级的 `images/` 目录，用相对路径引用：

![Hugo 目录结构示意](images/hugo-structure.png)

### Bilibili 视频

使用本站自定义 shortcode，传入 BV 号即可，播放器为 16:9 响应式布局：

{{< bilibili BV1GJ411x7h7 >}}

### YouTube 视频

使用 Hugo 内置 shortcode：

{{< youtube dQw4w9WgXcQ >}}

> **注意**：Bilibili 播放器默认关闭弹幕和自动播放；如需多 P 视频的某一集，
> 写成 `{{</* bilibili id="BV号" page="2" */>}}`。

## 小结

到这里，一篇包含代码、图片、视频的文章就完成了。
新建文章只需 `hugo new posts/tech/文章名/index.md`，然后开始写作。
