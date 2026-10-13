# `@akairos/milkdown-article-style`

Shared **article typography CSS** for Milkdown editor surfaces and WeChat article publishing.

> 💡 **设计说明**：本项目是作者 **Kairos 自己的公众号与 Milkdown 写作排版规范标准（Opinionated Default Standard）**。追求克制、舒适的呼吸感与杂志级排版质感。宿主应用与用户可以按需全量采用，或通过覆写 CSS 变量与选择器进行自由定制。

---

## 包含文件

| 文件 | 职责 |
| --- | --- |
| `article.css` | 核心正文排版（p / h1–h6 / 列表 / 代码块 / 引用 / 表格 / 篇章导读卡片 / 互动卡片 / 徽章 / 高亮 / 按键等） |
| `tokens-default.css` | 默认 `--wx-*` 主题变量令牌（sage-journal 质感与品牌基色） |

*纯 CSS 样式库，零运行时 JS 依赖。*

---

## 核心使用场景

| 项目 | 使用方式 |
| --- | --- |
| **@akairos/pipeline** | 在微信导出打包时引入 `article.css`（构建时 `?raw` 并通过 Juice 进行 HTML 内联化） |
| **Nezus 写作编辑器** | 在 Milkdown 编辑器中加载 `tokens-default.css` 与 `article.css` 实现沉浸式实时所见即所得 |

---

## 安装与引入

```bash
bun add @akairos/milkdown-article-style
# 或
pnpm add @akairos/milkdown-article-style
npm install @akairos/milkdown-article-style
```

在你的应用或 Milkdown 容器中引入：

```ts
import '@akairos/milkdown-article-style/tokens-default.css';
import '@akairos/milkdown-article-style/article.css';
```

---

## 自定义与覆写 (Customization)

如果想要定制自己的视觉风格，有以下几种简便方式：

### 1. 覆盖 CSS 变量令牌（简单调色）
在你的全局样式或 `.milkdown .editor` 上覆盖 `--wx-*` 变量：

```css
.milkdown .editor {
  --wx-brand-accent: #2563eb;       /* 替换品牌强调色 */
  --wx-soft-surface: #f8fafc;       /* 替换卡片柔和浅底色 */
  --wx-body-line-height: 1.9;       /* 调整正文行高 */
  --wx-body-letter-spacing: 0.02em; /* 调整字间距 */
}
```

### 2. 局部覆盖组件样式
通过专用类名直接接管：

```css
/* 自定义篇首导读卡片 */
.milkdown .editor .wechat-article-card-intro {
  border-radius: 12px;
  background-color: #f1f5f9;
}

/* 自定义导读字号 */
.milkdown .editor .wechat-article-card p {
  font-size: 13.5px;
}
```

---

## 许可证

MIT License © Kairos
