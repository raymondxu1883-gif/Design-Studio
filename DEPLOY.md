# 部署指南 / Deployment Guide

## 🚀 快速部署到 GitHub Pages

### 1. 在 GitHub 创建仓库

1. 登录 GitHub
2. 点击 "New Repository"
3. 命名为 `luminadesign-studio`（或你喜欢的名字）
4. 选择 Public
5. 不要初始化 README（我们已经有 README 了）

### 2. 推送代码到 GitHub

```bash
# 进入项目目录
cd /workspace/projects/workspace/studio-website

# 初始化 git
git init

# 添加所有文件
git add .

# 提交
git commit -m "Initial commit: Lumina Design Studio website"

# 添加远程仓库（替换 yourusername 为你的 GitHub 用户名）
git remote add origin https://github.com/yourusername/luminadesign-studio.git

# 推送
git push -u origin main
```

### 3. 配置 GitHub Pages

1. 进入你的 GitHub 仓库
2. 点击 "Settings" 标签
3. 左侧菜单选择 "Pages"
4. Source 选择 "GitHub Actions"
5. 点击 "Create your own workflow file"

创建工作流文件 `.github/workflows/deploy.yml`：

```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches: [ main ]
  workflow_dispatch:

permissions:
  contents: read
  pages: write
  id-token: write

concurrency:
  group: "pages"
  cancel-in-progress: false

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4
      
      - name: Setup Node
        uses: actions/setup-node@v4
        with:
          node-version: '20'
          cache: 'npm'
      
      - name: Install dependencies
        run: npm ci
      
      - name: Build
        run: npm run build
      
      - name: Setup Pages
        uses: actions/configure-pages@v4
      
      - name: Upload artifact
        uses: actions/upload-pages-artifact@v3
        with:
          path: './dist'

  deploy:
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    needs: build
    steps:
      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v4
```

### 4. 更新网站配置

编辑 `astro.config.mjs`，将 `site` 改为你的实际 URL：

```javascript
export default defineConfig({
  site: 'https://yourusername.github.io/luminadesign-studio', // 更新这里
  // ...
});
```

然后提交并推送：

```bash
git add astro.config.mjs
git commit -m "Update site URL"
git push
```

### 5. 等待部署完成

1. 进入仓库的 "Actions" 标签
2. 等待工作流运行完成（约 2-3 分钟）
3. 完成后访问 `https://yourusername.github.io/luminadesign-studio`

---

## ☁️ 部署到 Cloudflare Pages

### 方式 1: 通过 Git 集成（推荐）

1. 登录 [Cloudflare Dashboard](https://dash.cloudflare.com/)
2. 点击左侧 "Pages"
3. 点击 "Create a project"
4. 选择 "Connect to Git"
5. 授权 GitHub 并选择你的仓库
6. 构建设置：
   - **Build command**: `npm run build`
   - **Build output directory**: `dist`
   - **Root directory**: `/`
7. 点击 "Save and Deploy"

### 方式 2: 直接上传

1. 构建项目：`npm run build`
2. 登录 Cloudflare Pages
3. 创建项目 → "Direct Upload"
4. 上传 `dist` 文件夹中的所有文件

---

## 🔧 更新网站

以后每次更新代码后：

```bash
cd /workspace/projects/workspace/studio-website

# 修改代码...

# 提交并推送
git add .
git commit -m "描述你的修改"
git push
```

GitHub Actions 会自动重新部署网站！

---

## 📝 部署前检查清单

- [ ] 更新 `astro.config.mjs` 中的 `site` URL
- [ ] 更新 `src/layouts/Layout.astro` 中的站点信息
- [ ] 更新联系邮箱（`src/pages/contact.astro`）
- [ ] 添加真实的作品集图片到 `public/images/`
- [ ] 更新社交媒体链接（`src/components/Footer.astro`）
- [ ] 替换虚拟客户评价为真实评价
- [ ] 决定品牌名（当前是 "Lumina Design Studio"）

---

## 🆘 常见问题

### Q: 构建失败怎么办？
查看 GitHub Actions 日志，通常是：
- 依赖安装问题 → 删除 `node_modules` 和 `package-lock.json` 重新安装
- 代码语法错误 → 检查 Astro 文件语法

### Q: 样式没生效？
确保 `src/layouts/Layout.astro` 中导入了全局样式：
```astro
import '../styles/global.css';
```

### Q: 图片不显示？
- 检查图片路径是否正确
- GitHub Pages 区分大小写
- 确保图片已提交到仓库

---

## 📚 有用链接

- [Astro 部署指南](https://docs.astro.build/en/guides/deploy/)
- [GitHub Pages 文档](https://docs.github.com/en/pages)
- [Cloudflare Pages 文档](https://developers.cloudflare.com/pages/)

---

祝部署顺利！🎉
