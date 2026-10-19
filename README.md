# 画风库入口（GitHub Pages）

这个仓库只做一件事：给你一个**永远不变**的地址。

```
https://liyuan570.github.io/comfyui-gallery/
```

打开它，页面会读取 `latest.json` 里你电脑当前那条 Cloudflare 隧道的地址，
点「打开画风库」就跳过去。

## 为什么图片不在这里

- 图库是**活的**：能删除、能批量打包下载、有 ~970 张 2MB 原图（约 800MB）。
  GitHub Pages 是纯静态托管，放不了这些功能，也不适合放这么大的图。
- 所以：**入口在 Pages（稳定），内容在你电脑（实时）**。
- 本机的守护进程（`tunnel_supervisor.py`）会在公网地址变化时自动调用
  `publish_portal.py` 更新 `latest.json` 并推上来，所以你不用管这个仓库。

## 密钥

访问密钥**不写进仓库**。第一次打开时在页面上粘贴一次（`?k=` 后面那串），
之后存在浏览器的 localStorage 里。清掉浏览器数据需要重新贴一次。

## 更新机制

```
tunnel_supervisor.py  →  gallery/.tunnel_url
        ↓ 地址变化时
publish_portal.py     →  pages/latest.json  →  git push
        ↓
GitHub Pages 自动发布（约 1 分钟）
```
