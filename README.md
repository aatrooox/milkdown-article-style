# `@akairos/milkdown-article-style`

旧版 Milkdown / 微信正文样式兼容包。`0.1.3` 为最后一个维护版本，包含表头单行和横向滚动修复。

正文样式已迁入 `@akairos/myno@0.3.1`：新项目请引用 `@akairos/myno/article.css` 与 `@akairos/myno/tokens-default.css`，或 `@akairos/myno/style` 一次加载两者。已发布的旧版本继续可用。

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
| [myno](https://github.com/k7airos/myno) | 直接依赖本包，在编辑器与独立工作台加载正文样式，微信导出时内联 CSS |
| [zzhub-pipeline](https://github.com/k7airos/zzhub-pipeline) | 直接依赖本包，内置微信导出时引入 `article.css`；启用 myno 时使用插件构建的排版资源 |
| Nezus 写作编辑器 | 通过 myno 及共享样式包复用正文外观，是现有应用消费方 |

配套的 [Milkdown Article Plugins](https://github.com/k7airos/milkdown-article-plugins) 提供高亮、卡片、徽章和快捷键的语法与序列化；本包只提供 CSS，不负责解析 Markdown。[Kairos Skills](https://github.com/k7airos/kairos-skills) 中的 `milkdown-writing` 提供这些语法的写作说明。只想调样式和复制到公众号可使用 myno；需要完整草稿发布流程可使用 Pipeline。

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

本包无需 JavaScript 运行时、账号或 API 服务。微信不直接加载外部 CSS；发布时由 myno / Pipeline 等宿主将样式内联到 HTML。修改此包的 CSS 后，需要重建消费方的浏览器 bundle 并更新安装包，才能影响已构建的导出资源。

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
