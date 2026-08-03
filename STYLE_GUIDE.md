# LingoCamp — Design System & Style Guide

> 英语学习平台 · 美式80年代复古漫画风格  
> Last updated: 2026-08-03

---

## 1. Brand Identity

| 属性 | 值 |
|---|---|
| 品牌名 | **LingoCamp** |
| 定位 | "Learn English the Fun Way" — 游戏化英语学习 |
| 风格关键词 | 美式复古 · 80年代漫画 · 做旧印刷 · 怪奇物语 |
| 品牌人格 | 有趣、温暖、不拘一格、鼓励冒险 |
| 目标用户 | 8–25岁英语学习者，厌倦传统课堂 |

---

## 2. Color Palette

提取自 Hero 主视觉插画，由浅到深：

| 用途 | 色名 | Hex | RGB | 示意 |
|---|---|---|---|---|
| 页面底色 | Cream 奶油底 | `#FAE2B4` | 250, 226, 180 | ████████ |
| 卡片/模块底色 | Paper 纸张 | `#FFF8EE` | 255, 248, 238 | ████████ |
| 浅奶油 | Cream Light | `#FFF3E0` | 255, 243, 224 | ████████ |
| 点缀/强调 | Orange 焦橙 | `#D97B3F` | 217, 123, 63 | ████████ |
| CTA 按钮 | Brick Red 砖红 | `#CF6730` | 207, 103, 48 | ████████ |
| Hover 加深 | Brick Dark | `#B54E1A` | 181, 78, 26 | ████████ |
| 辅助点缀 | Olive 橄榄绿 | `#7A8450` | 122, 132, 80 | ████████ |
| 深色点缀 | Olive Dark | `#5C6635` | 92, 102, 53 | ████████ |
| 正文/暗色 | Navy 藏蓝 | `#1A2533` | 26, 37, 51 | ████████ |
| 副文/浅色 | Navy Light | `#2B3A55` | 43, 58, 85 | ████████ |
| 虚线装饰 | Halftone | `#E8D5B0` | 232, 213, 176 | ████████ |

**规则**：
- 大面积底色只用 Cream / Paper / Navy 三色
- Brick Red 和 Olive 仅用于按钮、标签、icon 点缀，不铺大面积
- Orange 仅用于高亮重点文字和 emoji 装饰，用色克制
- 绝不使用渐变背景，全部纯色块

---

## 3. Typography

| 层级 | 字体 | 用途 | 大小 |
|---|---|---|---|
| **Display / H1** | Fredoka One (cursive) | 首页大标题、Logo | `clamp(2.6rem, 5vw, 4.2rem)` |
| **H2 章节标题** | Fredoka One | Features / Courses / CTA | `2.2rem` |
| **H3 卡片标题** | Fredoka One | 功能卡、课程卡、Footer 小标题 | `1.2–1.3rem` |
| **Body / 正文** | Nunito (sans-serif) | 所有段落、列表、导航 | `0.9–1.2rem` |
| **按钮** | Fredoka One | CTA、链接按钮 | `1rem` |
| **数据/数字** | Fredoka One | Hero 统计数据 | `1.6rem` |

**字体加载**：Google Fonts CDN  
**Fallback**：系统 sans-serif

**规则**：
- Fredoka One 只用于标题和按钮，不在正文中使用
- 正文行高 `1.6`，标题行高 `1.12–1.15`
- 字母间距：标题 `-0.5px`，徽章文字 `1px`

---

## 4. Border & Shadow System

```
漫画感来自两个要素：粗边框 + 偏移投影
```

| 元素类型 | Border | Border-radius | Box-shadow |
|---|---|---|---|
| 功能卡片 | `3px solid #1A2533` | `12px` | `6px 6px 0 #1A2533` |
| 课程卡片 | `3px solid #1A2533` | `12px` | `6px 6px 0 #1A2533` |
| 评价卡片 | `3px solid #1A2533` | `12px` | `4px 4px 0 #1A2533` |
| 按钮 | `3px solid #1A2533` | `8px` | `4px 4px 0 #1A2533` |
| CTA Banner 徽章 | `2px solid #1A2533` | `20px` | `3px 3px 0 rgba(0,0,0,0.15)` |
| Icon 容器 | `2px solid #1A2533` | `12px` | — |
| Header 底线 | `3px solid #1A2533` | — | — |
| 章节分割线 | 6px dashed halftone 条 | — | — |

**Hover 交互**：
- 卡片：`translate(-2px, -2px)` + shadow 扩大 2px → 卡片"浮起来"
- 按钮：`translate(2px, 2px)` + shadow 缩小 2px → 按钮"按下去"

**规则**：
- 所有 border 统一 `#1A2533`（Navy），不使用不同颜色的边框
- 绝不使用圆角 `border-radius` 超过 `12px`

---

## 5. Layout & Spacing

| 区域 | 宽度 | 内边距 |
|---|---|---|
| 页面容器 | 无最大宽度（全宽） | 左右 `5%` |
| 内容网格（features/courses） | `max-width: 1100px` | 居中 |
| Hero 文字区 | `flex: 0 0 42%` | `3rem 5% 3rem 7%` |
| Hero 插图区 | `flex: 1` | — |
| Footer 网格 | `max-width: 1300px` | `3rem 5%` |
| Hero 最小高度 | `88vh` | — |
| 章节间距 | — | `5rem` 上下 |

**Hero 区特殊处理**：
- 插图裁掉左边空白区，与文字区接触
- 三层 CSS 渐变遮罩实现文字区 → 插图区的平滑过渡：
  1. `hero::after` — 全局渐变桥（cream → semi-transparent → transparent）
  2. `hero-grain` — 半调网点图案，仅在过渡带渐显
  3. `hero-visual::before` — 插图左边缘 80px 局部软遮罩
- 网点 mask 从透明 → 出现在大约 15% 宽处自然延伸到 30%，擦掉奶油色 → 图案过度僵硬感

---

## 6. Iconography

- 主要使用 **Emoji**（🎧 🎮 📖 👥 ★ ▶ →），与漫画风格的 playful 调性统一
- 不使用 Material / FontAwesome 等标准 icon 库的矢量图标
- 列表项标记统一使用 `★` 字符（Brick Red 色）
- 星级评分使用 `★` + `☆` 组合（Orange 色）

---

## 7. Illustrations

| 文件 | 路径 | 用途 | 尺寸 |
|---|---|---|---|
| hero-illustration.webp | `F:/测试/hero-illustration.webp` | Hero 主视觉 | 1100×880 |

**主视觉描述**：
- 橘黄色卷发小女孩，戴复古头戴耳机，趴地读绘本
- 周围散落：磁带、收音机、黑胶唱片、Game Boy
- 风格：80年代美式复古漫画，做旧印刷纸纹，半调网点
- 构图：人物偏右，与左侧文字区形成自然过渡

**生图提示词（V8 最终版）**：
> Vintage 1980s American comic book illustration with colored lineart: every object outlined in a darker shade of its own fill color; a little girl with messy orange wavy hair wearing chunky retro headphones, lying on the floor reading a picture book, cassette tapes, a boombox and vinyl records scattered around, warm peachy skin tone consistent across face arms and legs; rich saturated vintage colors: deep brick red, vivid navy blue, warm ochre orange, olive green; heavy paper grain, halftone print texture, risograph print effect; deep shadows, strong contrast, moody nostalgic atmosphere, retro zine aesthetic, 80s Americana; natural relaxed happy expression, small dot eyes; flat colors with dry-brush texture, absolutely no gradients; left third of image as empty aged cream paper; 16:9 landscape

**负面提示词**：
> glossy, shiny, 3D render, smooth digital airbrush, uniform line weight, perfect clean vector outlines, pastel colors, washed-out desaturated colors, Disney Pixar style, big sparkling eyes, round baby face, chubby cheeks, gradients, kawaii, modern cute children book style, face lighter than body skin

---

## 8. Page Structure

```
Header (sticky)
  ├── Logo (LingoCamp)
  └── Nav (Courses · Pricing · About · Blog · Log In)

Hero (min-height: 88vh)
  ├── .hero-grain (halftone bridge)
  ├── .hero-content (left 42%)
  │    ├── Badge (#1 English Learning Platform)
  │    ├── H1: "Speak English Like a Native"
  │    ├── P: subheadline
  │    ├── Button group (Start Free Trial + Watch Demo)
  │    └── Stats row (50K+ Learners · 4.9 Rating · 200+ Lessons)
  └── .hero-visual (illustration)

Divider (halftone stripe)

Features Section
  └── Grid (4 cards): Immersive Audio · Game Lessons · Story Curriculum · Speaking Club

Courses Section (paper bg)
  └── Grid (3 cards): Starter (Free) · Explorer ($12) · Master ($25)

Testimonials Section
  └── Grid (3 cards): rotating user reviews

CTA Banner (navy bg, radial gradient overlay)
  └── H2 + P + Big Button

Footer
  └── Grid (4 cols): Brand · Courses · Company · Support
  └── Footer bottom: copyright
```

---

## 9. CSS Animation Specs

（待实现 — 图层拆解阶段）

| 目标 | 计划动画 | 实现方式 |
|---|---|---|
| 整图 | 轻微上下浮动 | CSS `translateY` 缓动循环 |
| 双腿 | 以膝为轴左右摆动 | CSS `transform-origin` + `rotate` |
| 头发 | 微风飘动 | CSS `skewX` + `rotate` 组合 |
| 书页 | 风吹翻动 | CSS `scaleX` 伸缩模拟 |
| 背景 | 静止 | static |

---

## 10. Responsive Breakpoints

| 断点 | 行为 |
|---|---|
| `> 900px` | 默认布局：Hero 左右分栏，4列/3列网格 |
| `≤ 900px` | Hero 堆叠（文字居中 → 插图），网格缩减，隐藏导航 |

---

## 11. Tech Stack

| 层 | 技术 |
|---|---|
| 静态页面 | 纯 HTML5 + CSS3 |
| 字体 | Google Fonts (Fredoka One + Nunito) |
| 图片格式 | WebP（支持 alpha 的用 PNG） |
| 部署 | 待定 |
| 版本控制 | Git + GitHub |
