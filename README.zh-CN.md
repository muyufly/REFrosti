<div align="center">
  <img alt="Frosti Logo" src="https://github.com/EveSunMaple/Frosti/blob/main/docs/logo.png" width="280px">
  <br/><br/>
  <h1>REFrosti(Refined & EasyToPublish Frosti)</h1>
  <p><a href="./README.md">English</a> | <a href="./README.zh-CN.md">简体中文</a></p>
</div>

> **声明：** 本项目是基于 EveSunMaple 的优秀开源主题 [Frosti](https://github.com/EveSunMaple/Frosti) 深度开发和定制的高级版本。  
> 我在 Frosti 极速的 Astro 架构基础之上，全面引入了顶级的毛玻璃 (Glassmorphism) 美学设计、实时交互的数据可视化组件，以及突破性的全界面本地可视化发文 GUI 工具。

[![license](https://badgen.net/github/license/EveSunMaple/Frosti)](https://github.com/EveSunMaple/Frosti/blob/main/LICENSE)&nbsp;&nbsp;&nbsp;[![built with astro](https://badgen.net/badge/built%20with/Astro/ff5a03?icon=astro)](https://astro.build)

## ✨ 该版本有什么新特性？

除了继承自 Frosti 的强大基础特性（原生明暗双模、Pagefind 搜索、ViewTransitions 平滑切换、RSS）外，这个定制版还带来了以下史诗级革新：

- 🌌 **恒星数据统计 (`StarStatsCard`)**: 首页搭载了一个高达 60fps 帧率的 HTML5 Canvas 轨道模拟器。它会为您发布的**每一篇文章**生成一颗散发着脉冲光晕的行星。所有的轨道都完美适配浏览器容器的大小，颜色自动提取并同步当前的亮暗主题。
- 🪟 **高级毛玻璃 UI (Glassmorphism)**: 核心组件（包含 `MainCard`, `CategoryGrid`）已被彻底重构。现在支持高级背景虚化、浮动交互交互阴影，并开启了硬件级别的 CSS 渲染加速以保证动画顺滑无比。
- 🚀 **Blog Publisher 博客发布器**: 业界首创的、开箱即用的本地可视化仪表盘系统，完全消灭了手动编写 YAML 和终端口令的繁琐流程。

---

## 🚀 Blog Publisher 独立发布器 (本版核心独占)

发布文章不应该像是写代码一样痛苦。为此，我们为你预装了一个彻底剥离了第三方依赖的纯 Node.js 服务端可视化编辑器。让您发布 Markdown 博客就如同在社交软件发帖一样丝滑简单。

### 快速开始：

1. **启动发布器**:
   在项目根目录下打开终端，输入以下命令：
   ```sh
   pnpm run publish
   ```
2. **打开仪表盘**:
   浏览器前往 **`http://localhost:3721`** 即可进入专属发布后台。

### 核心工作流：
- **拖拽即上传**: 将你的 `.md` / `.mdx` 文件拖入左侧识别区，将封面或插图图片拖入右侧。系统会精准地将它们分发存入 `src/content/blog/` 和 `public/image/` 目录。
- **可视化 Frontmatter 表单**: 仪表盘会瞬间解析您的 Markdown 文件，并展开一个清爽的表单界面。你可以随时在 UI 上调整您的**标题、撰写日期、分类、标签串以及封面图路径**，甚至一键设定为草稿，无需再触碰任何原始 YAML 代码。
- **一键极速发布**: 在下方输入你的本次更新留言，点击 **🚀 Publish (发布)** 按钮。后台就会替你自动跑完 `git add .`、`git commit` 以及最终推送至 GitHub 的全套流程。博客秒上线！

*(注：发布器运行在完全独立的 3721 端口。因此，当你在边写边预览时，你可以同时运行 `pnpm run publish` 和 `pnpm run dev` 互不干扰！)*

---

## ⬇️ 安装项目与本地预览

1. 全局安装 pnpm 包管理器（如果您尚未安装）
```sh
npm i -g pnpm
```

2. 安装本项目依赖
```sh
pnpm i
```

3. 生成全局搜索索引，并开启本地博客预览
```sh
# 生成供页面搜索器使用的索引文件
pnpm run search:index

# 启动 Astro 本地服务 (通常为 http://localhost:4321)
pnpm run dev
```

---

## ✒️ 文章字段说明 (Frontmatter Schema)

如果您是一位硬核用户，依然习惯不用 GUI 工具直接手写文件，您可以遵循以下的元数据配置：

|    名称    |       含义       | 必须 |
| :---------: | :-----------------: | :------: |
|    title    |    文章标题    |   是    |
| description | 文章简短描述 |   是    |
|   pubDate   |  发布日期   |   是    |
|    image    | 封面图路径 (/image/...) |    否    |
| categories  | 文章分类集合  |    否    |
|    tags     |    文章标签集合     |    否    |
|    badge    |    角标提示文本    |    否    |
|    draft    |    是否为未公开发布的草稿     |    否    |

> [!TIP]
> - 你可以通过设置 `badge` 属性为 `Pin` 来置顶或特别标记你的文章。
> - 只要设置了 `draft: true` 就会将文章冻结在草稿状态，打包与生产环境概不显示。

---

## 🔧 项目基础配置 (`frosti.config.yaml`)

Frosti 使用直观的 `frosti.config.yaml` 充当其核心配置中枢。

### 网站全局信息配置
```yaml
site:
  tab: BlogRefined # 浏览器标签页名字
  title: BlogRefined # 实际网站大标题
  description: A clean, elegant, and interactive blog template
  language: zh # 非常重要，请使用"zh"或"en"激活对应本土化词典
  favicon: /favicon.ico
```

### 主题与高亮设定
```yaml
theme:
  light: winter  # 基于 daisyUI 的明亮模式主题名
  dark: dracula  # 基于 daisyUI 的黑暗模式主题名
  code: github-dark # 基于 Shiki 强大的代码块高亮风格
```

### 侧导航与底部菜单
```yaml
menu:
  - id: home
    text: 首页
    href: /
    svg: "material-symbols:home-outline-rounded" # 使用开源 Iconify 字符图标集
    target: _self
```

#### 多语言机制
由于 `site.language` 被设定，界面上的大量文案将自动前往 `src/i18n/translations.yaml` 里查找匹配的词典，修改该文件即可定制属于你的各种固定文案。

---

## 💬 评论系统挂载

- **Waline 配置教程**: https://frosti.saroprock.com/blog/adding-comment-systems
- **修改自定风格**: 仓库在 `src/styles/waline.scss` 里提供了一份完全契合该主题视觉特征的默认评论样式表。您随时可以覆写它。

---

## 🎉 特别鸣谢

- **毫无保留且最为真挚的感谢给到原作者 [EveSunMaple](https://github.com/EveSunMaple/Frosti)**，您非凡卓越的开源 Frosti 主题框架是我们构建一切的灵魂基石。
- 给到速度突破极限的框架底层系统 [Astro](https://astro.build/) 。
- 给到 CSS 规则化神级工具 [Tailwind CSS](https://tailwindcss.com/) 和极简 UI 库 [daisyUI](https://daisyui.com/)。
