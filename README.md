# xtunnel-workers

本仓库是 [xtunnel](https://github.com/EthanPeng-2048/xtunnel) 的**构建产物仓库**——自动生成，勿手改。

- `_worker.js`：源仓库 `npm run build` 的单文件产物（esbuild 打包 + minify 变量名混淆），四个页面 HTML 已内嵌
- 更新方式：源仓库 `main` 分支 push → GitHub Actions（`.github/workflows/sync-artifact.yml`）校验并构建 → 自动提交推送本仓库
- 产物无变化时跳过提交

## Cloudflare 部署

1. Workers & Pages → Create application → Pages → **Connect to Git** → 选本仓库
2. 构建命令**留空**（输出目录 `/`）；输出根的 `_worker.js` 自动以高级模式运行
3. 绑定 KV：设置 → 绑定 → KV 命名空间，变量名 **KV**
4. 环境变量（生产）：**ADMIN** = 管理密码（可选 `KEY` / `UUID` / `PROXYIP`）
