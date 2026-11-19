# quarto-book-themes

为中文长文（教材 / 讲义 / 书籍）设计的两个 [Quarto](https://quarto.org) 主题扩展：

| 主题 | format 名 | 风格 |
|---|---|---|
| **Genesis Book** | `genesis-book-html` | litera 底座：无衬线正文 + 衬线标题，冷灰目录面板 |
| **Paper Book** | `paper-book-html` | journal 底座：全衬线正文（纸书观感），纸色目录面板 |

## 安装与使用

```bash
quarto add dontreadthisline/quarto-book-themes
```

安装时会在两个主题间让你选择（或全部安装）。然后在文档 front matter 或项目 `_quarto.yml` 中使用：

```yaml
---
title: 我的文档
format: genesis-book-html    # 或 paper-book-html
---
```

注意 format 名的 `-html` 后缀是 Quarto 定位扩展的约定（剥离后缀即扩展目录名），必须完整书写。

## 主题包含什么

**中文长文排版**：系统字体栈（PingFang SC / Noto Sans SC 等）、行高 1.85、衬线标题层级、教材风表格（上下粗边框去竖线）、代码紧凑化、块级公式横向滚动防溢出、行内公式基线修正（不撑行距）。

**三栏布局**（桌面 ≥992px）：目录面板贴住视口左缘（无 Quarto 默认 70px inset 留白）、右侧页内目录贴住右缘、正文居中并保持 44-46rem 阅读行长；页脚章节导航与正文列对齐。窄屏自动回退 Quarto 原生抽屉。

**阅读模式**：目录面板右缘有一个抽屉把手（或按 `[` 键），一键收起两侧目录——正文加宽为 58rem 容器、右侧留白区安置本章小节导航（复用 Quarto 原生 scroll-spy 滚动高亮）。状态由 localStorage 记忆，翻页保持。

## 已知边界

- 数学公式渲染使用 Quarto 默认的 MathJax CDN（联网环境正常）。若需完全离线，参考[本仓库的讨论](../../issues)自行替换为本地自托管 MathJax。
- 三栏 grid 覆盖与阅读模式依赖 Quarto 1.4+ 的 DOM 结构；开发与测试于 Quarto 1.8.27。
- 阅读模式的窄屏（<1200px）形态为居中单栏（右导航放不下自动隐藏）。

## 结构

```
genesis-book/
├── _extension.yml        扩展声明（format: genesis-book-html）
├── theme.scss            三栏布局 + 主题适配层
├── _typography.scss      通用中文排版（纯 CSS 语法，可拷出以 .css 用于任意网站）
└── sidebar-toggle.html   阅读模式注入（把手 + 布局切换 + localStorage）
paper-book/               同构
```

## 许可

MIT
