# Silas Guo 的个人知识库

使用 Hugo + hugo-book 主题构建的个人知识库。

## 项目结构

```
goodmangll.github.io/
├── archetypes/       # 内容模板
│   ├── default.md    # 通用默认模板
│   ├── post.md       # 博客文章模板
│   ├── docs.md       # 文档页面模板
│   └── section.md    # 章节目录模板
├── content/          # 网站内容
│   ├── posts/        # 博客文章
│   └── docs/         # 知识库文档
│       ├── technical/  # 技术文档
│       ├── engineering/ # 工程实践
│       └── ai/         # AI 技术
├── themes/           # 主题（hugo-book 子模块）
├── hugo.toml         # 配置文件
└── public/           # 构生成输出
```

## Hugo Archetypes

Archetypes 是 Hugo 的内容模板，用于 `hugo new` 命令时自动填充 Front Matter。

### 查找顺序

1. `archetypes/<content-type>.md`
2. `archarctypes/default.md`
3. 内置默认模板

### 模板变量

| 变量 | 说明 |
|------|------|
| `{{ .`Date }}` | 当前日期时间 |
| `{{ .File.ContentBaseName }}` | 文件名（不含扩展名） |
| `{{ .Date.Format "2006-01-02" }}` | 格式化日期 |

### hugo-book 主题 Front Matter 字段

| 字段 | 用途 |
|------|------|
| `weight` | 调整菜单中项目的顺序 |
| `bookFlatSection` | 标记页面为扁平化章节 |
| `bookCollapseSection` | 隐藏嵌套的章节/页面（仅文件树菜单） |
| `bookHidden` | 隐藏页面/章节从侧边菜单 |
| `bookToC` | `false` 时隐藏目录 |
| `bookSearchExclude` | `true` 时排除页面从搜索索引 |

### 项目中的 Archetypes

#### post.md - 博客文章

```toml
+++
title = '{{ replace .File.ContentBaseName "-" " " | title }}'
date = '{{ .Date }}'
categories = ["技术"]
tags = []
weight = 100
+++
```

#### docs.md - 知识库文档

```toml
+++
title = '{{ replace .File.ContentBaseName "-" " " | title }}'
bookFlatSection = false
bookToC = true
bookSearchExclude = false
weight = 100
+++
```

#### section.md - 章节目录

```toml
+++
title = '{{ replace .File.ContentBaseName "-" " " | title }}'
bookCollapseSection = false
bookHidden = false
weight = 100
+++
```

## 使用方法

```bash
# 创建博客文章
hugo new posts/my-new-post.md

# 创建文档
hugo new docs/technical/new-doc.md

# 创建章节
hugo new docs/ai/new-section/_index.md

# 启动开发服务器
hugo server
```

## 参考资料

- [Hugo 官方文档](https://gohugo.io/)
- [hugo-book 主题](https://github.com/alex-shpak/hugo-book)
- [Archetypes 文档](https://gohugo.io/content-management/archetypes/)

---

生成时间：2026-02-04
