# 部署到Cloudflare Pages

## 配置说明

本项目已配置为可在Cloudflare Pages上部署的静态网站。以下是部署步骤：

## 部署到Cloudflare Pages

1. 在Cloudflare Dashboard中创建一个新的Pages项目
2. 连接到你的GitHub/GitLab仓库
3. 在"Build & deployments"部分，使用以下设置：
   - Framework preset: `None`
   - Build command: `echo "Static site, no build required"`
   - Build output directory: `./`
   - Root directory: `/`

## 静态资源配置

项目包含以下配置文件以优化静态部署：

- `_headers` - 设置HTTP响应头和缓存策略
- `_redirects` - 将所有路由重定向到index.html（支持SPA路由）
- `vercel.json` - Vercel部署配置（可选）
- `static.json` - Netlify等平台的部署配置（可选）

## 国际化功能

国际化功能已优化，支持在静态环境中正常工作：
- 语言选择不再导致页面刷新
- 语言设置保存在cookie中
- 所有语言文件都可在languages/目录下找到

## 功能说明

此应用是一个Persona 5风格的名片生成器，完全在浏览器中运行，无需服务器端处理。