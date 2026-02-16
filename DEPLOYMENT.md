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

- **Cloudflare Pages 默认域名**：
  - ✅ **go-6ut.pages.dev**（新项目，推荐使用）
    - 项目名称：go
    - 简短易记，适合推广
  - 🗑️ **silly-love-gateway.pages.dev**（旧项目，可选择保留或删除）
    - 项目名称：slove
    - 较长，不便推广

- **自定义域名配置**（可选）：
  - ✅ **推荐方案**：使用 sillylove.indevs.in 的子域名
    - 例如：go.sillylove.indevs.in 或 gateway.sillylove.indevs.in
    - 需要在 Indevs.in 管理面板添加子域名 CNAME 记录
    - Target: `go-6ut.pages.dev`

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


## 自定义域名配置详解

### 当前状态（2026-02-16）

1. **新项目信息**：
   - 项目名称：go
   - 默认域名：go-6ut.pages.dev ✅ 已部署并验证
   - GitHub 仓库：Ylsssq926/silly-love-gateway
   - 状态：正常运行

2. **旧项目信息**：
   - 项目名称：slove
   - 默认域名：silly-love-gateway.pages.dev
   - 状态：可选择保留或删除

3. **域名说明**：
   - Cloudflare Pages 的默认域名在项目创建时确定，基于项目名称
   - 新项目使用 "go" 作为名称，获得更短的域名 go-6ut.pages.dev
   - 后缀 "-6ut" 是 Cloudflare 自动生成的唯一标识符

### 推荐解决方案

使用 **sillylove.indevs.in** 的子域名：

#### 方案 A：go.sillylove.indevs.in

1. 登录 Indevs.in 管理面板：https://domain.stackryze.com/
2. 添加子域名 CNAME 记录：
   - 子域名：go
   - 目标：silly-love-gateway.pages.dev
3. 在 Cloudflare Pages 添加自定义域名：go.sillylove.indevs.in

#### 方案 B：gateway.sillylove.indevs.in

1. 登录 Indevs.in 管理面板
2. 添加子域名 CNAME 记录：
   - 子域名：gateway
   - 目标：silly-love-gateway.pages.dev
3. 在 Cloudflare Pages 添加自定义域名：gateway.sillylove.indevs.in

### 为什么不能使用 slove.pages.dev？

Cloudflare Pages 的默认域名（*.pages.dev）是在项目**首次创建**时确定的，基于当时的项目名称。即使后来重命名项目，默认域名也不会自动更改。

要获得 slove.pages.dev 域名，需要：
1. 删除当前项目
2. 重新创建名为 "slove" 的新项目
3. 重新连接 GitHub 仓库并部署

但这会导致短暂的停机时间，不推荐。

### 清理未完成的域名配置

如果需要删除 go.sillylove.com 配置：

1. 进入 Cloudflare Pages 项目页面
2. 点击 "Custom domains" 标签
3. 找到 go.sillylove.com
4. 点击右侧的菜单按钮（三个点）
5. 选择 "Remove"
