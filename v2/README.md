# MIRROR V2 项目结构

## 目录说明

```
v2/
├── index.html              # 首页
├── feature.html            # 特稿栏目页
├── design.html             # 设计栏目页
├── fragments.html          # 碎片列表页（独立更新，不按期刊）
├── archive.html            # 往期期刊列表页
├── spectrum.html           # 光谱归档页
│
├── css/                    # 模块化 CSS
│   ├── base.css            # 基础样式（变量、导航、页脚、简单文章布局）
│   ├── index.css           # 首页专属（spine、cover、columns）
│   ├── article-long.css    # 长文章通用样式（设计、特稿等）
│   ├── feature.css         # 特稿列表页专属
│   ├── design.css          # 设计列表页专属
│   ├── fragments.css       # 碎片页专属
│   ├── archive.css         # 往期页专属
│   ├── spectrum.css        # 光谱页专属
│   └── design-article.css  # 设计文章专属（已合并到 article-long.css）
│
├── issues/                 # 期刊整页（按期刊归档）
│   ├── issue-01.html       # 第一期"亲密"概览页
│   └── issue-02.html       # 第二期（预留）
│
├── issue-01/               # 第一期文章内容（按栏目分类）
│   ├── people/
│   │   └── mirror-self.html
│   ├── refraction/
│   │   └── algorithm-choice.html
│   ├── design/
│   │   └── chatbox-corner.html
│   └── fragments/
│       ├── 01-navigation.html
│       ├── 02-ai-understand.html
│       └── 03-voice-input.html
│
├── fragments/              # 碎片文章（独立更新）
│   ├── 01/
│   ├── 02/
│   ├── 03/
│   └── 04/
│
└── docs/                   # 文档
    └── design-editorial-guide.md  # 设计栏目编辑手册
```

## CSS 使用指南

| 页面类型 | 引用 CSS |
|---------|---------|
| 首页 | `base.css` + `index.css` |
| 特稿列表 | `base.css` + `feature.css` |
| 设计列表 | `base.css` + `design.css` |
| 碎片列表 | `base.css` + `fragments.css` |
| 往期 | `base.css` + `archive.css` |
| 光谱 | `base.css` + `spectrum.css` |
| 长文章（设计/特稿） | `base.css` + `article-long.css` |
| 简单文章（碎片） | `base.css`（包含基础 article 样式） |

## 路径规则

### CSS 引用
- 根目录页面：`./css/xxx.css`
- issues/ 目录内：`../css/xxx.css`
- issue-01/ 目录内：`../../css/xxx.css`

### 链接规则
- 首页 → 期刊页：`./issues/issue-01.html`
- 期刊页 → 首页：`../index.html`
- 期刊页 → 文章：`../issue-01/people/xxx.html`
- 文章 → 期刊页：`../issues/issue-01.html`（视文件位置而定）

## 更新策略

### 碎片（Fragments）
- 不绑定特定期刊
- 独立更新，最新内容放最前
- Fragment 编号按发布顺序递增

### 期刊（Issues）
- 每季度发布一期
- 有明确的主题和选文
- 期刊概览页放在 `issues/issue-XX.html`
- 文章放在 `issue-XX/栏目/文章.html`

## 栏目英文名

| 中文 | 英文 | 说明 |
|-----|------|------|
| 镜中人 | people | 封面故事/人物特写 |
| 折射 | refraction | 深度报道/Feature |
| 设计 | design | 设计观察/批判 |
| 碎片 | fragments | 短篇观察（不按期刊更新） |
| 光谱 | spectrum | 每期延伸书单 |

## 文章样式说明

### 简单文章（base.css）
- 用于碎片等短篇
- 基础标题、正文样式
- 无引用块、参考文献等特殊样式

### 长文章（article-long.css）
- 用于设计、特稿等长文
- 包含：
  - 大号标题（52px）
  - Lead 段落突出
  - 引用块（左侧橙色边框）
  - 参考文献列表
- 类名使用通用 `.article-*` 前缀

### 标题斜体高亮
如需在标题中使用彩色斜体突出关键词，添加 `.highlight` 类：
```html
<h1 class="article-title">
  标题文字<em class="highlight">突出部分</em>
</h1>
```
