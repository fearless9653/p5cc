# 部署到Cloudflare Pages

## 配置说明

本项目是纯静态网站，无需构建步骤，可直接部署到Cloudflare Pages。

## 部署步骤

1. 在Cloudflare Dashboard中创建一个新的Pages项目
2. 连接到你的GitHub/GitLab仓库
3. 在"Build & deployments"部分，使用以下设置：
   - Framework preset: `None`
   - Build command: （留空）
   - Build output directory: `./`
   - Root directory: `/`

## 静态资源配置

- `_headers` - 设置HTTP响应头：
  - HTML/JS/CSS/JSON使用`max-age=0, must-revalidate`，发布后用户立即可见更新（Cloudflare边缘节点仍通过ETag协商缓存保证性能）
  - `assets/`目录（字体、卡片底图等不常变动的素材）使用一年长缓存
  - 安全头：CSP（含Cloudflare Web Analytics所需的`connect-src`）、`X-Content-Type-Options`、`Referrer-Policy`、`frame-ancestors`

注意：本项目没有客户端路由，因此不需要`_redirects`的SPA兜底规则——保留真实的404有助于及早发现资源路径错误。

## 本地开发

```bash
pnpm install
pnpm start   # http-server，默认 http://localhost:8080
```

## 国际化功能

- 语言切换不刷新页面，直接重新加载语言文件
- 语言设置保存在cookie中，首次访问按浏览器语言自动选择
- 语言文件位于`languages/`目录，加载失败时回退到中文

## 功能说明

此应用是一个Persona 5风格的名片生成器，完全在浏览器中运行，无需服务器端处理。
