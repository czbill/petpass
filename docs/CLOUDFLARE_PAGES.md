# 把隐私政策挂到 https://petpass.dev

> **完整教程（购买域名 → Pages 部署 → 绑定域名）已整理到工程根目录：**  
> [`docs/CLOUDFLARE_DOMAIN_AND_PAGES.md`](../../docs/CLOUDFLARE_DOMAIN_AND_PAGES.md)

目标链接（填 App Store Connect）：

**https://petpass.dev/privacy**

（`/privacy.html` 与首页也会到同一页）

---

## 前提

1. 域名 `petpass.dev` 已在 Cloudflare 购买/托管（Nameservers 用 Cloudflare）
2. 本仓库已推到 **GitHub**（公开或私有均可；审核员打开的是你的域名网页）
3. 本地已有 `docs/privacy.html`、`docs/index.html`（无需 `_redirects`：Pages 原生把 `privacy.html` 服务在 `/privacy`，加反向重定向会循环）

若还没推送：

```bash
cd /Users/zhibiaochen/Desktop/develop/PetPass/github
git status
# git remote add origin https://github.com/<你的用户名>/<pages-repo>.git
# git add docs
# git commit -m "Add privacy policy for App Store"
# git push -u origin main
```

---

## A. 用 Cloudflare Pages 部署（推荐）

### 1. 创建 Pages 项目

1. 打开 [Cloudflare Dashboard](https://dash.cloudflare.com)
2. 左侧 **Workers & Pages** → **Create** → **Pages** → **Connect to Git**
3. 授权并选择包含本 `docs/` 的仓库
4. 配置：

| 项 | 值 |
|----|-----|
| Project name | `petpass`（随意） |
| Production branch | `main` |
| Framework preset | **None** |
| Build command | **留空** |
| Build output directory | **`docs`** |

5. **Save and Deploy** → 得到 `https://<项目名>.pages.dev`

先打开 `https://<项目名>.pages.dev/privacy.html` 确认页面正常。

### 2. 绑定自定义域名 petpass.dev

1. Pages 项目 → **Custom domains** → **Set up a custom domain**
2. 输入：`petpass.dev`
3. 按提示确认（同账号下一般会自动加 DNS）
4. 可选：`www.petpass.dev`
5. 等到状态 **Active**

### 3. 验证

- https://petpass.dev/privacy  
- https://petpass.dev/privacy.html  
- https://petpass.dev/

通过后填入 App Store Connect Privacy Policy URL。

---

## B. 更新隐私政策

1. 改 `docs/privacy.html`
2. `git push`
3. Pages 自动重新部署

---

## 常见问题

**默认 Cloudflare 页 / 打不开** → Custom domain 未 Active，或 DNS 冲突。  
**/docs/privacy.html 404** → 正确路径是 `/privacy.html`。  
**完整步骤与购域名说明** → 见 [`docs/CLOUDFLARE_DOMAIN_AND_PAGES.md`](../../docs/CLOUDFLARE_DOMAIN_AND_PAGES.md)

---

## App 对齐

- 邮箱：`support@petpass.dev`
- 文件：`docs/privacy.html`
