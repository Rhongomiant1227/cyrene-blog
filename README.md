# Cyrene Blog

昔涟主题静态博客，基于 [matsuzaka-yuki/mizuki](https://github.com/matsuzaka-yuki/mizuki) 进行本地定制与重构，当前版本主要围绕《崩坏：星穹铁道》角色“昔涟 / Cyrene”的官方无水印素材来统一界面风格。

在线地址：

- GitHub 仓库：[Rhongomiant1227/cyrene-blog](https://github.com/Rhongomiant1227/cyrene-blog)
- GitHub Pages：[https://rhongomiant1227.github.io/cyrene-blog/](https://rhongomiant1227.github.io/cyrene-blog/)

## 项目说明

这个仓库不是原版 Mizuki，也不是单纯换了一张横幅的套皮。

当前项目保留了 Mizuki 的 Astro 静态博客架构、组件体系和部署方式，同时完成了这些定制：

- 将站点标题、简介、导航、公告和个人资料改为昔涟主题
- 使用项目内本地素材重构首页横幅、头像、贴纸和壁纸资源
- 为 GitHub Pages 子路径 `/cyrene-blog/` 修正了部署配置和链接生成
- 保留 Astro + Pagefind + GitHub Actions 的静态站点工作流

## 与 Mizuki 的关系

本项目基于 Mizuki 继续开发，核心主题框架与不少页面能力来自上游项目：

- 上游项目：[matsuzaka-yuki/mizuki](https://github.com/matsuzaka-yuki/mizuki)
- 原始技术栈：Astro、Tailwind CSS、Svelte、Pagefind

这里的目标不是抹掉上游来源，而是明确说明：

- `Mizuki` 是底层主题框架来源
- `Cyrene Blog` 是当前这个仓库的成品名称和定制方向

## 本地开发

要求：

- Node.js 22 或更高
- pnpm 9 或更高

安装依赖：

```bash
pnpm install
```

启动本地开发服务器：

```bash
pnpm dev
```

默认访问地址：

```text
http://127.0.0.1:4321/
```

## 构建

生产构建命令：

```bash
pnpm build
```

这个命令会依次执行：

1. 更新番剧数据脚本
2. Astro 生产构建
3. Pagefind 搜索索引生成
4. 字体压缩脚本

产物目录为：

```text
dist/
```

## 部署到 GitHub Pages

当前仓库已经内置 GitHub Actions 工作流，目标是发布到：

```text
https://rhongomiant1227.github.io/cyrene-blog/
```

关键配置已经按子路径部署处理好：

- `PUBLIC_BASE_PATH=/cyrene-blog/`
- `PUBLIC_SITE_URL=https://rhongomiant1227.github.io/cyrene-blog/`
- 自动部署分支：`pages`

GitHub 仓库 Pages 设置需要选择：

- `Source`: `Deploy from a branch`
- `Branch`: `pages`
- Folder: `/(root)`

## 如何更新博客

这个项目当前是静态博客，不是后台投稿系统。

更新方式是：

1. 本地修改文章或页面内容
2. 本地预览确认效果
3. 提交到 Git
4. 推送到 GitHub
5. 等待 GitHub Actions 自动重新构建并发布

常用命令：

```bash
pnpm new-post your-post-name
pnpm dev
git add .
git commit -m "Update content"
git push
```

文章主要放在：

```text
src/content/posts/
```

专题页面内容通常在：

```text
src/content/spec/
```

## 主题素材

当前昔涟主题资源以本地文件为准，主要放在：

```text
public/assets/cyrene/
```

建议继续保持这条原则：

- 优先使用官方公开素材
- 尽量使用无水印版本
- 新增素材时保持裁切、清晰度和页面比例一致
- 需要额外定制的装饰元素，再单独放入 `derived/` 之类的派生目录

## 目录参考

几个关键文件：

- `src/config.ts`：站点主配置
- `astro.config.mjs`：Astro 与站点基础路径配置
- `.github/workflows/deploy.yml`：GitHub Pages 自动部署
- `public/assets/cyrene/`：昔涟主题素材

## 许可与致谢

本项目基于 Mizuki 继续定制开发，请保留对上游项目的说明与尊重。

- Mizuki: [matsuzaka-yuki/mizuki](https://github.com/matsuzaka-yuki/mizuki)
- Astro: [https://astro.build](https://astro.build)

如果后续继续公开发布，建议同时保留：

- 当前仓库自己的主题说明
- 上游主题来源说明
- 原始许可证文件
