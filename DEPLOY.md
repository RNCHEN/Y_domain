# 运维笔记(内部用,hiring manager 请看 README)

## 架构

- 域名 **wangyouyou888.com**:Squarespace 注册,DNS 指向 GitHub Pages
  - 4 条 A 记录 @ → 185.199.108–111.153;CNAME www → rnchen.github.io
- 托管:GitHub Pages(本仓库 `main` 分支根目录),HTTPS 已启用
- 单页静态站:`index.html`(内联 CSS/JS,无框架、无构建)
- `assets/`:简历 PDF + 头像(720px 压缩版)
- 根目录的源材料 PDF / 原图已 gitignore,不会发布

## 日常更新流程

```sh
# 1. 本地预览
python3 -m http.server 8642     # 打开 http://localhost:8642,改完强刷

# 2. 上线
git add -A && git commit -m "说明" && git push
# 1–2 分钟自动部署;进度看 https://github.com/RNCHEN/Y_domain/actions
```

## 已知坑

- Pages 偶发 "Deployment failed, try again later" = GitHub 后端瞬时故障,
  Actions 页 Re-run 或推空 commit 重试即可
- CDN 缓存约 10 分钟,刚部署完看不到就无痕窗口或强刷
- 在 GitHub 网页上改过 Custom domain 会自动生成 CNAME commit,本地先 `git pull` 再推
