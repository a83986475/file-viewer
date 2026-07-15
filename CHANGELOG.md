# Changelog

完整对外更新日志见 [docs/changelog.md](docs/changelog.md)。

## File Viewer v2.1.30 — 2026-07-15

这个版本统一了 Full 包的完整资产交付方式。仅执行 `npm install` 只会安装 renderer 代码，不会自动把 Worker、WASM、字体和 vendor 资源发布到业务站点；未完成资产交付时，不属于完整格式支持。

官方 8 个 Full 包：

- `@file-viewer/web-full`
- `@file-viewer/vue3-full`
- `@file-viewer/vue2.7-full`
- `@file-viewer/vue2.6-full`
- `@file-viewer/react-full`
- `@file-viewer/react-legacy-full`
- `@file-viewer/svelte-full`
- `@file-viewer/jquery-full`

交付规则：

- Vite：安装同版本 `@file-viewer/vite-plugin`，使用 `fileViewerRenderers({ copyAssets: true })`，dev/build 自动发布完整资源。
- Webpack、Rspack、Rollup、Vue CLI、Umi：运行 Full 包自带的同版本 CLI：`npx --no-install file-viewer-copy-assets ./public/file-viewer`。
- `@file-viewer/web-full`：直接使用 CDN/IIFE，或原样部署完整 `dist/` 目录时无需复制；只复制入口 IIFE 不是完整部署。

已覆盖 8 个 Full 包合约、10 组框架冷安装浏览器矩阵、Vue 2.6 / Vue CLI 3、Vite dev/build、非 Vite 复制 CLI 和 `web-full` 完整 `dist/` 回归。

### Upgrade

Vite：

```bash
pnpm add @file-viewer/vue3-full@2.1.30
pnpm add -D @file-viewer/vite-plugin@2.1.30
```

```ts
fileViewerRenderers({ copyAssets: true })
```

非 Vite：

```bash
pnpm add @file-viewer/vue3-full@2.1.30
npx --no-install file-viewer-copy-assets ./public/file-viewer
```

## 维护模板

后续发布说明继续使用“用户为什么升级”的结构：

```md
## File Viewer vX.Y.Z

这次主要改进 [场景] 的体验。

### 适合升级的人

- 使用 [框架/包/部署方式] 的项目
- 遇到 [具体问题] 的项目

### Highlights

- 修复 / 改进 [用户可感知变化]
- 更新 Demo、Docs、离线资源或组件 README

### Upgrade

pnpm add @file-viewer/vue3-full@latest
```
