# `@zzclub/milkdown-article-style`

Shared **article typography** for Milkdown surfaces that should match WeChat
export output.

| File | Role |
| --- | --- |
| `article.css` | p / h1–h6 / list / code / table / … under `.milkdown .editor` |
| `tokens-default.css` | default `--wx-*` variables (sage-journal / default account) |

**Not** a Milkdown plugin — pure CSS, zero runtime JS.

## Consumers

| Project | How |
| --- | --- |
| **zzhub-pipeline** | Import `article.css` into the export browser bundle (`?raw` + Juice) |
| **Nezus** | Import tokens + article in `MilkdownEditor` for live writing preview |

## Install

### Local (sibling checkouts under `core/`)

```json
"@zzclub/milkdown-article-style": "file:../milkdown-article-style"
```

### Published registry (after first publish)

```bash
pnpm add @zzclub/milkdown-article-style
# or
bun add @zzclub/milkdown-article-style
```

```ts
import '@zzclub/milkdown-article-style/tokens-default.css'
import '@zzclub/milkdown-article-style/article.css'
```

## Ownership

- **Design source of truth:** this package.
- Host apps may override chrome only (editor shell, `note:` links, toolbars).
- Do not fork `article.css` into consumers.

## Release

```bash
# bump version in package.json, then:
npm publish --access restricted   # or public, if desired
```

Consumers bump the dependency version when styles change.
