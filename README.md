# Y_domain — Youyou Wang 个人域名网站

加州执业药师(PharmD, RPh)的个人 portfolio,参照专业临床医师个人站的结构:执照注册信息、按执业场景分组的经历、发表文献、简历预览/下载。

## 现状:已全部上线 ✅

- [x] 域名:**wangyouyou888.com**(注册商 Squarespace,DNS 已指向 GitHub Pages)
- [x] 网站建成:`index.html`(单页静态站,无框架)
- [x] 简历 PDF 上线:页面内点击预览 + 下载(`assets/YouyouWang_CA_Pharmacy_Resume.pdf`)
- [x] 仓库:https://github.com/RNCHEN/Y_domain (GitHub Pages, main 分支根目录)
- [x] HTTPS 生效;`rnchen.github.io/Y_domain` 自动 301 到正式域名
- [x] 隐私:页面不含电话/邮箱,联系方式仅 LinkedIn(原版简历 PDF 内仍含完整联系方式,属有意保留)

## 文件结构

```
Y_domain/
├── index.html                              # 整站(HTML + 内联 CSS/JS)
├── assets/
│   └── YouyouWang_CA_Pharmacy_Resume.pdf   # 简历原件(页面预览/下载用)
├── README.md
└── *.pdf(根目录)                           # 源材料,已 gitignore,不发布
```

## 部署教程:GitHub Pages + Squarespace DNS

静态单页,选 GitHub Pages:免费、HTTPS 自动、git push 即发布。域名留在 Squarespace,只改 DNS 记录指过来。

### 第 1 步:推到 GitHub

```sh
# 在 GitHub 网页上新建一个 public 仓库(名字随意,如 portfolio),然后:
git add -A && git commit -m "Portfolio site"
git remote add origin https://github.com/<你的用户名>/<仓库名>.git
git push -u origin main
```

### 第 2 步:开启 GitHub Pages

GitHub 仓库页 → **Settings → Pages** → Source 选 **Deploy from a branch** → Branch 选 `main` / `/ (root)` → Save。
一两分钟后 `https://<用户名>.github.io/<仓库名>/` 就能访问。

### 第 3 步:GitHub 侧绑定自定义域名

同一个 Pages 设置页 → **Custom domain** 填你的域名(如 `example.com`)→ Save。
这会自动在仓库里生成一个 `CNAME` 文件(内容就是域名,一行)。

### 第 4 步:Squarespace 侧配 DNS

Squarespace 登录 → **Domains → 你的域名 → DNS Settings**,添加 5 条记录:

| 类型 | Host | 值 |
|---|---|---|
| A | @ | 185.199.108.153 |
| A | @ | 185.199.109.153 |
| A | @ | 185.199.110.153 |
| A | @ | 185.199.111.153 |
| CNAME | www | `<你的用户名>.github.io` |

注意:Squarespace 域名默认带一些指向 Squarespace 自己的预设记录(A/CNAME 指 Squarespace 服务器的),要**删掉**,否则解析冲突。

### 第 5 步:开 HTTPS

DNS 生效后(几分钟到几小时),回到 GitHub Pages 设置页,勾选 **Enforce HTTPS**。
如果勾选框是灰的,等 DNS 传播完再来——GitHub 要先验证域名指向才能签证书。

### 之后每次更新

```sh
git add -A && git commit -m "更新内容" && git push
```

push 完约 1 分钟自动上线,没有别的步骤。

## 本地预览

```sh
open index.html            # 直接用浏览器打开
python3 -m http.server     # 或 http://localhost:8000
```
