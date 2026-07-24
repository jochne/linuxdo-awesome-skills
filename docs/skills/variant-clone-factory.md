# variant-clone-factory

## 快速判断

`variant-clone-factory` 用于把 **Variant 共享模板链接**复刻为可下载的 React 工程。它不是从截图猜测界面，而是按 Capture、Classify、Codegen、Package ZIP、Visual QA 的流水线抓取目标模板、生成工程并检查视觉差异。

## 适合场景

- 你有一个可访问的 Variant 共享模板，想导出为可继续开发的 React 工程。
- 你需要快速搭建有权使用的营销页、仪表盘、登录页、卡片站或应用壳原型。
- 你希望用 Web UI 或 CLI 反复提交模板链接，并把结果保存为 ZIP。
- 你需要用像素差异检查复刻结果，而不只看肉眼是否相似。

## 前置要求

- 可访问的 Variant 共享模板链接。
- Docker + Docker Compose（推荐），或 Node.js/npm 本地运行环境。
- 运行环境能够访问 `variant.com`；VPS 无法直连时需配置 `HTTP_PROXY` / `HTTPS_PROXY`。
- 可运行 Chromium/Playwright 的本地机器或 VPS；官方建议小流量 VPS 至少 2 核 CPU、4GB 内存和 20GB 磁盘。

## 输入与输出

输入：

- Variant 共享模板 URL。
- 可选 API Key、代理、端口和任务目录配置。

输出：

- React 工程 ZIP，默认位于 `jobs/<jobId>/artifact.zip`。
- Web UI、API 或 CLI 的任务结果。
- 可选视觉验收产物和像素差异结果。

## 核心特色

- 页面抓取到工程导出：流水线覆盖 Capture、Classify、Codegen、Package ZIP 与 Visual QA。
- React 目标：输出可继续开发的 React 工程，而不是仅导出截图或静态图片。
- 视觉验收：可生成像素差异结果，作为是否接近目标模板的检查依据。
- 双入口：单容器同时提供 Web UI、API 与 Playwright，也可用 `npm run clone -- <Variant 共享链接>` 走 CLI。
- 部署友好：提供 Docker Compose、环境变量、健康检查和 Nginx 反代说明。

## 和相近技能的差异

- 相比 [image-to-code-skill](image-to-code-skill.md)，`variant-clone-factory` 的输入是可访问的 Variant 共享页面，会生成完整 React 工程；前者的输入是 UI 图片、截图或 Figma 导出稿，重点在图片切图与设计还原。
- 相比通用网页爬虫，它不以采集内容为目标，而是把 Variant 模板转成可运行的前端工程。
- 相比设计模板生成器，它不凭提示词生成新界面，核心是对既有模板进行复刻和视觉验收。

## 工作流程

1. 部署服务或安装本地依赖，确认能访问 `variant.com`。
2. 在 Web UI 或 CLI 提交 Variant 共享模板链接。
3. Capture 阶段抓取目标页面。
4. Classify 阶段识别页面结构与类型。
5. Codegen 阶段生成 React 工程。
6. Package ZIP 阶段将工程打包至任务目录。
7. Visual QA 阶段按需输出视觉差异结果，检查复刻效果。

## 当前限制

- 仅面向 Variant 共享链接，不支持把任意网页直接纳入同一流程。
- 当前输出为 React 工程；作者在 Linux.do 回复中明确 Vue 尚未适配。
- 目标访问、网络代理、Chromium/Playwright 运行状态会直接影响执行结果。
- `1:1` 是项目目标而非无条件保证，仍应根据视觉验收结果和实际业务需要复核。
- 应只处理有权使用或复刻的模板；原仓库当前未声明许可证，复用或分发前需自行确认授权。

## 链接

- 项目仓库：<https://github.com/lulistart/variant-clone-factory>
- 收录来源：<https://linux.do/t/topic/2642041>
- 原项目说明：<https://github.com/lulistart/variant-clone-factory/blob/main/README.md>
- 部署说明：<https://github.com/lulistart/variant-clone-factory/blob/main/DEPLOY.md>

## 备注

本页基于 Linux.do 来源、原项目 README、DEPLOY.md、package.json 与 GitHub 元数据提炼而成。原项目是可部署的 Web 应用和 CLI，未提供可直接安装到 Codex 的 `SKILL.md`；帖子原文只用于整理阶段理解用途、特色、流程和局限性，不作为仓库存档内容保留。
