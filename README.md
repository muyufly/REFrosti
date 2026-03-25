<div align="center">
  <img alt="Frosti Logo" src="https://github.com/EveSunMaple/Frosti/blob/main/docs/logo.png" width="280px">
  <br/><br/>
  <h1>BlogRefined / Frosti (Custom Edition)</h1>
</div>

> **Notice:** This project is a heavily customized and enhanced fork of the original [Frosti Theme by EveSunMaple](https://github.com/EveSunMaple/Frosti).  
> We have built upon Frosti's incredible Astro performance to introduce premium glassmorphism aesthetics, dynamic interactive data visualizations, and a groundbreaking zero-dependency local GUI Publisher.

[![license](https://badgen.net/github/license/EveSunMaple/Frosti)](https://github.com/EveSunMaple/Frosti/blob/main/LICENSE)&nbsp;&nbsp;&nbsp;[![built with astro](https://badgen.net/badge/built%20with/Astro/ff5a03?icon=astro)](https://astro.build)

## ✨ What's New in This Version?

In addition to Frosti's foundational features (Light/Dark mode, Pagefind, ViewTransitions, RSS), this custom edition introduces:

- 🌌 **Starfield Statistics (`StarStatsCard`)**: A 60fps HTML5 Canvas orbital simulation on the homepage. It dynamically renders a pulsing glowing star for **every single article** you publish. The orbits perfectly adapt to the container size, and the colors automatically sync with your current Light/Dark theme.
- 🪟 **Premium Glassmorphism UI**: Core components (`MainCard`, `CategoryGrid`) have been completely redesigned with high-end backdrop blurs, floating interactive shadows, and hardware-accelerated CSS rendering to ensure silky smooth performance.
- 🚀 **Blog Publisher GUI**: A beautifully designed, standalone local visual dashboard that completely eliminates the need for manual markdown YAML writing and terminal git commands.

---

## 🚀 The Blog Publisher GUI (Stand-alone Tool)

Publishing articles shouldn't feel like programming. We've included a completely standalone, zero-dependency Node.js visual editor that makes publishing markdown blogs as easy as posting on social media.

### 快速开始 (How to Use):

1. **Start the Publisher**:
   Open a terminal in the project directory and run:
   ```sh
   pnpm run publish
   ```
2. **Open the Dashboard**:
   Go to **`http://localhost:3721`** in your browser to view the Publisher GUI.

### 核心工作流 (Workflow):
- **Drag & Drop**: Drag and drop your `.md` / `.mdx` files into the left zone. Drop your cover images or inline pictures into the right zone. Files are automatically routed to `src/content/blog/` and `public/image/` respectively.
- **UI Frontmatter Editor**: The dashboard instantly parses your markdown file and opens a clean visual form. Edit your **Title, Date, Description, Images, Categories, and Tags** without ever touching raw YAML formatting.
- **One-Click Publish**: Enter a commit message (or leave it blank), click **🚀 Publish**, and the tool will automatically execute `git add .`, `git commit -m "..."`, and `git push`. Your blog is live instantly!

*(Note: The Publisher runs on a separate port from Astro. You can run `pnpm run publish` and `pnpm run dev` simultaneously!)*

---

## ⬇️ Installation & Local Development

1. Install pnpm package manager (if you haven't already)
```sh
npm i -g pnpm
```

2. Install project dependencies
```sh
pnpm i
```

3. Generate search index & Start development server
```sh
# Generate the search index for Pagefind
pnpm run search:index

# Start the Astro development server (http://localhost:4321)
pnpm run dev
```

---

## ✒️ Article Information (Frontmatter Schema)

If you still prefer writing articles manually without the GUI Publisher, use this YAML header format:

|    Name     |       Meaning       | Required |
| :---------: | :-----------------: | :------: |
|    title    |    Article title    |   Yes    |
| description | Article description |   Yes    |
|   pubDate   |  Publication date   |   Yes    |
|    image    | Article cover image |    No    |
| categories  | Article categories  |    No    |
|    tags     |    Article tags     |    No    |
|    badge    |    Article badge    |    No    |
|    draft    |    Draft status     |    No    |

> [!TIP]
> - You can pin your article by setting the `badge` property to `Pin`
> - Setting `draft: true` will mark the article as a draft, preventing it from appearing in production builds.

---

## 🔧 Configuration (`frosti.config.yaml`)

Frosti uses `frosti.config.yaml` as its core configuration file.

### Website Basic Information
```yaml
site:
  tab: BlogRefined # Browser tab text
  title: BlogRefined # Website title
  description: A clean, elegant, and interactive blog template
  language: en # e.g., "en" or "zh"
  favicon: /favicon.ico
```

### Theme Settings
```yaml
theme:
  light: winter  # Light mode daisyUI theme
  dark: dracula  # Dark mode daisyUI theme
  code: github-dark # Shiki code block theme
```

### Menu & Navigation
```yaml
menu:
  - id: home
    text: Home
    href: /
    svg: "material-symbols:home-outline-rounded" # Iconify string
    target: _self
```

#### Multi-Language Support
Configure interface text translations inside `src/i18n/translations.yaml` based on your `site.language` code.

---

## 💬 Comment System

- **Tutorial (Waline)**: https://frosti.saroprock.com/blog/adding-comment-systems
- **Custom styles**: A default, site-matching comment stylesheet is provided at `src/styles/waline.scss`.

---

## 🎉 Acknowledgements

- **First and foremost, massive thanks to [EveSunMaple](https://github.com/EveSunMaple/Frosti)** for creating the incredibly fast and robust original Frosti Template.
- [Astro](https://astro.build/) for the insanely fast web framework.
- [Tailwind CSS](https://tailwindcss.com/) & [daisyUI](https://daisyui.com/) for the styling engines.
