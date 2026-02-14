# Hugo 博客

基于 [Hugo](https://gohugo.io/) 与 [PaperMod](https://github.com/adityatelange/hugo-PaperMod) 主题的静态博客。

## 前置要求

- 安装 [Hugo](https://gohugo.io/installation/)（建议 Extended 版）
- 安装 [Git](https://git-scm.com/)（用于拉取主题）

### 使用 winget 安装（Windows）

在 PowerShell 或终端中执行（若弹出 UAC 请选择“是”）：

```powershell
# 安装 Git
winget install --id Git.Git -e --accept-source-agreements --accept-package-agreements

# 安装 Hugo Extended（建议先装完 Git 再执行）
winget install --id Hugo.Hugo.Extended -e --accept-source-agreements --accept-package-agreements
```

安装完成后**重新打开终端或 Cursor**，使 `git` 和 `hugo` 加入 PATH。验证：

```powershell
git --version
hugo version
```

若仍报错「无法将 git 项识别为 cmdlet」：说明已安装但当前终端未刷新 PATH。在**当前终端**执行下面一行后再试（或直接关闭 Cursor 再打开）：

```powershell
$env:Path = [System.Environment]::GetEnvironmentVariable("Path","Machine") + ";" + [System.Environment]::GetEnvironmentVariable("Path","User")
```

## 安装主题

首次使用需先安装 PaperMod 主题。在项目根目录执行：

```bash
git init
git submodule add https://github.com/adityatelange/hugo-PaperMod.git themes/PaperMod
```

或手动克隆到 `themes/PaperMod`：

```bash
git clone https://github.com/adityatelange/hugo-PaperMod.git themes/PaperMod
```

## 本地开发

```bash
hugo server -D
```

`-D` 会包含草稿文章。浏览器打开 http://localhost:1313/ 预览。

也可使用 npm：

```bash
npm run dev
```

## 构建静态站

```bash
hugo
```

生成的网站在 `public/` 目录，可部署到任意静态托管（如 GitHub Pages、Netlify、Vercel）。

```bash
npm run build
```

## 新建文章

基于模板创建新文章：

```bash
hugo new posts/文章文件名.md
```

编辑生成的 `content/posts/文章文件名.md`，填写 frontmatter（`title`、`description`、`date` 等）和正文。将 `draft: true` 改为 `draft: false` 后即可在正式构建中显示。

文章模板位于 `archetypes/default.md`，可按需修改以统一新文章的 frontmatter。
