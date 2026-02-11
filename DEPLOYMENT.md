# 部署指南

## Cloudflare Pages 部署步骤

### 1. 登录 Cloudflare Dashboard

访问：https://dash.cloudflare.com/

### 2. 进入 Pages 页面

点击左侧菜单的 "Workers & Pages"

### 3. 创建新项目

1. 点击 "Create application"
2. 选择 "Pages" 标签
3. 点击 "Connect to Git"

### 4. 连接 GitHub 仓库

1. 选择 "GitHub" 作为 Git provider
2. 授权 Cloudflare 访问 GitHub（如果首次使用）
3. 选择 `Ylsssq926/silly-love-gateway` 仓库

### 5. 配置构建设置

- **Project name**: `silly-love-gateway`（或自定义名称）
- **Production branch**: `main`
- **Build command**: (留空)
- **Build output directory**: `/`
- **Root directory**: (留空)

### 6. 部署

点击 "Save and Deploy"，等待部署完成。

### 7. 配置自定义域名（可选）

部署完成后，在项目设置中添加自定义域名：

1. 进入项目 → Settings → Custom domains
2. 点击 "Set up a custom domain"
3. 输入域名（建议使用）：
   - `go.sillylove.com`
   - `start.sillylove.com`
   - `gateway.sillylove.com`
4. 按照提示配置 DNS 记录

## 访问地址

部署完成后，你将获得：

- Cloudflare Pages 默认域名：`silly-love-gateway.pages.dev`
- 自定义域名（如果配置）：`go.sillylove.com`

## 更新部署

每次推送到 `main` 分支，Cloudflare Pages 会自动重新部署。

```bash
git add .
git commit -m "更新导航页"
git push origin main
```

## 注意事项

1. 确保 GitHub 仓库是公开的，或者 Cloudflare 有访问权限
2. 自定义域名需要在 Cloudflare DNS 中配置
3. 部署通常需要 1-2 分钟完成
4. 可以在 Cloudflare Dashboard 查看部署日志和状态
