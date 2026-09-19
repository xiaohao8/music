# 桌面歌词 · 官网与隐私政策

`Desktop-sing`（桌面歌词）的静态站点，用 **Netlify** 部署。
仓库里就是可部署的成品：**没有构建步骤、没有依赖**，Netlify 直接把仓库根目录当发布目录。

## ⚠️ 这是部署副本，源文件在主仓库

站点的**源文件在主仓库 [xiaohao8/Desktop-sing](https://github.com/xiaohao8/Desktop-sing)
的 `site/` 目录**，官网截图等资源也由那边的脚本生成（`site/tools/make_assets.py`
依赖主仓库的 `preview/`，在本仓库里单独跑不起来）。

**不要在本仓库直接改页面** —— 下次同步会被覆盖。改法：在主仓库改 `site/`，
再跑一次 `python sync_site.py` 把改动同步过来（脚本会校验两边逐字节一致）。

## 页面

| 文件 | 用途 |
|---|---|
| `index.html` | 官网首页（功能 / 下载 / 常见问题） |
| `privacy.html` | **隐私政策（中文）** |
| `privacy.en.html` | **隐私政策（英文）** |
| `assets/` | 样式、脚本、官网截图与图标 |
| `netlify.toml` | Netlify 部署配置（发布目录 + 缓存策略） |

`privacy.html` / `privacy.en.html` 这两个地址要填进 **Microsoft Store 提审表单的
「隐私政策 URL」**（商店政策 10.5.1 要求 Win32 / Desktop Bridge 产品必须始终具备隐私政策），
所以**这两个文件的路径和文件名不要改**，改了等于让商店表单里的链接失效。

## 部署（Netlify）

1. Netlify → **Add new site → Import an existing project** → 选 GitHub →
   首次会要求授权 Netlify 访问仓库（可只授权本仓库）。
2. 构建设置：`netlify.toml` 已写好，**Build command 留空、Publish directory = `.`**，
   正常情况下不用手改。
3. 部署完成后把站点地址填进商店表单：
   - 中文 listing → `https://<站点名>.netlify.app/privacy.html`
   - 英文 listing → `https://<站点名>.netlify.app/privacy.en.html`
4. 如有自定义域名，**优先用自定义域名**填商店表单（比 `*.netlify.app` 更稳、更可信），
   换域名时记得同步改商店表单里的地址。

部署后自查一遍：

- 无痕窗口打开两个隐私政策地址：能正常显示、无需登录、正文完整（中文 8 节）；
- 打开首页：截图与样式正常 —— **截图 404 基本都是 `assets/` 没同步上去**；
- 按一遍「下载」按钮：国内网盘与 GitHub 两个渠道都能跳。

## 许可证与声明

本站点内容随 `Desktop-sing` 项目一并发布。
第三方许可、字体与致谢见主仓库
[NOTICE.md](https://github.com/xiaohao8/Desktop-sing/blob/main/NOTICE.md)。
