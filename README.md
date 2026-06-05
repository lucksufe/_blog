# _blog

极简静态博客系统。纯 HTML/CSS/JS，零依赖、零构建、开箱即用。

支持 Markdown 写作、数学公式（KaTeX）、图表（Mermaid）、代码高亮、多主题切换、图片上传。可部署到 GitHub Pages 或本地服务器。

## 快速开始

### 本地服务器

```bash
# 克隆仓库
git clone https://github.com/lucksufe/_blog.git
cd _blog

# 启动服务器
python3 server.py

# 带密码保护
python3 server.py --password mysecret

# 自定义端口
python3 server.py 3000
```

打开 `http://localhost:8080` 即可看到博客首页。

### GitHub Pages

1. Fork 本仓库
2. 进入仓库 Settings → Pages
3. Source 选择 `main` 分支，目录选 `/ (root)`
4. 等待几分钟，通过 `https://你的用户名.github.io/_blog` 访问

## 写文章

打开 `http://localhost:8080/editor/write.html`（本地模式）或你的 GitHub Pages 地址 + `/editor/write.html`。

- **本地模式** — 自动检测本地服务器，无需 Token
- **GitHub 模式** — 需要 Fine-grained Personal Access Token（Contents: Read and write 权限）

编辑器支持：
- Markdown 工具栏，快速插入格式
- 数学公式工具栏，插入 LaTeX 模板
- 图表工具栏，插入 Mermaid 流程图/时序图
- 粘贴/拖拽图片自动上传
- 自动保存草稿（每 30 秒）
- 发布前预览

写完点「发布」，文章自动保存并出现在首页。

## 目录结构

```
_blog/
├── index.html          # 首页（文章列表 + 标签筛选）
├── post.html           # 文章详情页
├── server.py           # 本地服务器（Python，零依赖）
├── config.json         # 博客配置（标题、语言等）
├── themes.json         # 主题配色定义（7 套主题）
├── rss.xml             # RSS 订阅（发布文章时自动生成）
├── favicon.svg
├── LICENSE             # MIT
├── css/
│   ├── style.css       # 博客样式
│   └── pages.css       # 着陆页样式
├── js/
│   ├── app.js          # 首页逻辑
│   ├── post.js         # 文章渲染
│   ├── theme.js        # 主题切换
│   ├── i18n.js         # 国际化
│   └── vendor/         # CDN 离线回退（内网部署用）
├── editor/
│   ├── write.html      # 写文章页面
│   ├── index.html      # 文章管理页面
│   ├── js/
│   │   ├── write.js    # 编辑器逻辑
│   │   ├── manage.js   # 管理页逻辑
│   │   ├── github.js   # GitHub 存储适配器
│   │   └── local.js    # 本地存储适配器
│   └── posts/
│       └── _example.md # 文章模板
├── pages/
│   ├── blog.html       # 项目着陆页
│   ├── tutorial.html   # 使用教程
│   └── usecases.html   # 使用场景
└── posts/
    └── manifest.json   # 文章索引（自动生成）
```

## 功能

### 写作

- **Markdown** — 完整语法支持，配合工具栏快捷插入
- **数学公式** — KaTeX 渲染，行内 `$...$` / 块级 `$$...$$`
- **Mermaid 图表** — 流程图、时序图、甘特图等
- **代码高亮** — Prism.js，支持 Python/JS/C/C++/Bash 等
- **图片上传** — 粘贴或拖拽自动上传

### 管理

- **标签分类** — 按标签筛选文章
- **全文搜索** — 首页搜索框
- **草稿系统** — 自动保存 + 手动存为草稿
- **密码保护** — 本地服务器可选密码认证

### 主题

7 套主题，点击右上角切换：

| 主题 | 风格 |
|------|------|
| 暗色 | 默认深色 |
| 亮色 | 浅色背景 |
| 护眼绿 | 柔和绿色 |
| 紫悦 | 紫色调 |
| 云宝 | 青蓝色 |
| 柔柔 | 粉色 |
| 珍奇 | 淡紫色 |

主题定义在 `themes.json`，添加新主题只需增加一个 JSON 条目。

### RSS

自动生成 `rss.xml`，支持 RSS 阅读器订阅。

## 技术栈

全部通过 CDN 加载，无需 npm install。CDN 失败时自动回退到本地 `js/vendor/` 备份。

| 库 | 用途 |
|------|------|
| [marked.js](https://github.com/markedjs/marked) | Markdown 解析 |
| [KaTeX](https://katex.org) | 数学公式渲染 |
| [Mermaid](https://mermaid.js.org) | 图表渲染 |
| [Prism.js](https://prismjs.com) | 代码高亮 |

## 部署方式

### GitHub Pages（推荐）

推送到 GitHub，在 Settings → Pages 选择分支和目录即可。

### 本地服务器

```bash
python3 server.py
```

适合局域网使用，支持密码保护。编辑器自动检测本地服务器，无需 GitHub Token。

### 内网部署

将整个目录部署到内网服务器，`js/vendor/` 目录包含所有 CDN 库的离线备份，无需联网。

## License

MIT
