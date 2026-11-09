# AGENTS.md

本文件为在本仓库中工作的 AI Agent 提供指引.

## 仓库概览

本仓库是个人博客 "华航笔记" 的源码, 基于 Jekyll 构建. 站点通过 GitHub Pages 发布到 https://blog.huahang.im, 自定义域名由 `CNAME` 文件配置. 文章用中文写, 放在 `_posts/` 下. 主题是 `minima`. 仓库里没有自定义的 layout / include / sass, 主题资源全部来自 gem.

## 常用命令

- `bundle install`: 安装 gem 依赖.
- `bundle exec jekyll serve`: 启动本地开发服务器. 加 `--livereload` 可开启实时刷新.
- `bundle exec jekyll build`: 把静态站点构建到 `_site/`.
- `bundle exec jekyll post "Title"`: 在 `_posts/` 下新建文章 (由 jekyll-compose 提供).
- `bundle exec jekyll draft "Title"` / `bundle exec jekyll publish _drafts/...`: 草稿工作流.

注意: `jekyll serve` 不会自动重新加载 `_config.yml`. 修改 `_config.yml` 后要重启 `jekyll serve`.

## 架构说明

- `_config.yml` 固定 `url: https://blog.huahang.im`, 并启用以下插件: `jekyll-admin`, `jekyll-compose`, `jekyll-feed`, `jekyll-seo-tag`, `jekyll-sitemap`. Markdown 引擎是 `kramdown`.
- `Gemfile` 锁定 `jekyll ~> 4.4.1` 和 `minima ~> 2.5.2`, 另外锁定了 `ffi`. `minima` 2.5.2 是已发布的最新版, 3.x 尚未发布.
- 这是 Jekyll 4.x 站点, 不使用 GitHub Pages 自带的 Jekyll 版本. `Gemfile` 里的 `github-pages` gem 是有意注释掉的.
- Ruby 版本固定为 2.7.8 (见 `.ruby-version`). 因此 Sass 只能用 `jekyll-sass-converter` 3.0.0 和 `sass-embedded` 1.63.x. 更新的版本要求 Ruby >= 3.1.
- `_config.yml` 设置了 `sass.sourcemap: development`. 生产构建 (`JEKYLL_ENV=production`) 不输出 `main.css.map`.
- `_posts/` 中的文章按 `YYYY-MM-DD-slug.md` 命名, 使用标准的 Jekyll front matter. 内容以中文为主.
- Markdown 里的资源链接 (例如 `![alt](/resources/...)`) 要保留中文和空格的原始 UTF-8 写法, 不要做 URL 编码. Kramdown / Jekyll 在渲染时会处理编码. 原始路径也更方便作者阅读和编辑.
- 仓库没有测试和 linter. CI 是 GitHub Actions 的 `.github/workflows/jekyll-build.yml`. 推送到 `master`, 向 `master` 提交 PR, 或手动触发 (workflow_dispatch) 时, CI 会构建站点. PR 只构建, 不部署. 其他情况构建后会部署到 GitHub Pages.
- 近期提交大多是内容修改, 以及 Dependabot 对间接依赖 gem (例如 addressable, rack) 的版本升级.

## Git 约定

- 提交信息必须遵循 [Conventional Commits](https://www.conventionalcommits.org/) 格式 (例如 `feat:`, `fix:`, `chore:`, `docs:`, `build(deps):`).
- 提交时总是加 sign-off (`git commit -s`), 让提交信息带上 `Signed-off-by:` trailer.
