# Version 0.1.0

## Project Memory

- 这个项目是一个以本地维护为优先的 Linux.do 社区 skill 索引。
- 当前项目路径：`/Users/xlzhao/Documents/Github 项目咨询/linuxdo-awesome-skills/`。
- Git 仓库根目录已经迁移到 `linuxdo-awesome-skills/` 内部；后续所有 `git status`、提交和推送都必须在该目录执行，不要在父目录 `/Users/xlzhao/Documents/Github 项目咨询/` 操作。
- `data/skills/*.json` 是事实来源，README 和静态页面是展示层。
- GitHub Pages 自定义域名：`https://linuxdo-awesome-skills.tencents.ltd/`；README 的网页入口使用“在线导航页面”作为链接名称。
- README 面向最终读者显示，只保留项目定位、网页入口、技能清单、分类导航和阅读说明。
- 与本项目储备、编写过程、数据结构、发布计划、收录方法相关的内容放在 `CLAUDE.md` 或 `docs/collection-policy.md`，不要放进 README。
- README 表格列优先服务筛选和跳转；避免同时放“用途”和“适合场景”这类语义重复的长列。
- README 和静态页可展示 `前置要求`，用于帮助读者快速判断是否需要特定模型、API、本地脚本、后端服务或素材条件；保持短语化，不写安装教程。
- README 表格下方的技能简介可附 `description`，来源为原项目 `SKILL.md` frontmatter 的 description；中文 description 优先使用原文，英文 description 直译为中文，不做提炼总结。除非原始 description 特别长或同一项目包含多个子 skill description，否则不做整理归纳。
- README 表格不展示平台字段，统一按通用技能介绍；项目地址、Star 数、来源论坛分别独立成列。
- 来源论坛可使用 Linux.do favicon 图标：`https://cdn3.ldstatic.com/optimized/4X/c/c/d/ccd8c210609d498cbeb3d5201d4c259348447562_2_32x32.png`。
- GitHub README 不支持运行 JS 动态展示 star；可用 Shields.io 等外部图片徽章展示 GitHub 仓库和 star 数，但数值会有缓存延迟。
- README 中项目入口优先使用 GitHub 徽章和 star 徽章，增强在线阅读时的可扫读性。
- README 和静态页不展示 `status` 字段；正式收录条目默认按已核验终稿呈现。
- 结构化数据不再使用顶层 `status` 字段，改用 `verified_at` 和 `verification_sources` 记录核验信息。
- 单条 skill 的完整介绍放在 `docs/skills/`，详情页至少要让人快速看懂用途、适合场景、输入输出、核心特色、限制和来源。
- 静态页面入口为 `index.html`，用于后续发布到 GitHub Pages。
- 静态页的“详情”按钮使用 GitHub `blob/main` 的 Markdown 渲染页，不直接打开 GitHub Pages 上的 `.md` 源文件；待 Read the Docs 实际发布并确认可访问后，再集中替换 `getRenderedDetailUrl`。
- Read the Docs 入口配置为根目录 `.readthedocs.yaml`，使用 `mkdocs.yml` 构建 `docs/` 文档站；新增技能时必须同步 MkDocs 导航和 `docs/index.md`。
- 仓库结构：`data/skills/*.json` 保存结构化数据，`docs/skills/` 保存单条 skill 详情页，`index.html` 保存静态展示页面。
- 收录原则：只收录 Linux.do 社区用户发布的 skill；来源链接可以保留访问限制说明，例如 Linux.do `Lv1` 登录后可查看。
- 帖子原文只用于提炼 skill 的用途、特色、流程和局限性，不收录原文、不保存本地转录。
- `index.html` 不展示 Linux.do 来源权限提示，例如 Lv1、登录后可查看、可能需要权限；这些只保留在 JSON 或详情页。
- 静态页应优先高屏效比索引体验：卡片短、标签小、前置要求可扫读、限制只显示一句提醒，完整说明放详情页。
- `index.html` 除页内锚点外的跳转链接默认使用 `target="_blank"` 和 `rel="noopener noreferrer"`，避免读者离开导航页。
- 项目校验命令：`npm run check`。提交前必须运行，覆盖 JSON 解析、必填字段、README/静态页/详情页数量一致、本地链接、读者视图禁用词和内联 JS 语法。

## Maintenance Workflow

新增技能时按以下顺序执行：

1. 阅读 Linux.do 来源和原 GitHub 项目，优先确认 README、`SKILL.md`、示例、限制、许可证或特殊前置要求。
2. 新增 `data/skills/<id>.json`。字段至少包含 `id`、`name`、`author`、`repository`、`detail_page`、`verified_at`、`verification_sources`、`source`、`tags`、`one_liner`、`prerequisites`、`skill_description`、`use_cases`、`summary`、`workflow`、`limitations`、`notes`。
3. 新增 `docs/skills/<id>.md`。必须讲清：快速判断、适合场景、前置要求、输入输出、核心特色、和相近技能的差异、工作流程、当前限制、链接、备注。
4. 更新 `README.md` 技能清单和对应分类简介。README 面向最终读者，不写维护过程、不放帖子原文。
5. 更新 `index.html` 的 `skills` 数组、筛选标签和统计数字。不要在静态页展示来源权限提示。
6. 更新 `mkdocs.yml` 和 `docs/index.md`，确保 Read the Docs 文档站包含新增技能详情页。
7. 更新 `CLAUDE.md` 的条目记忆，尤其记录和相近技能的差异化定位、不可忽略的授权/商业限制、来源访问限制。
8. 更新 `CHANGELOG.md`。
9. 运行 `npm run check`，必要时再用浏览器打开 `index.html` 做冒烟检查。

发布或提交前检查：

- `npm run check`
- `git status --short`
- 确认没有 `.DS_Store`、`.playwright-mcp/`、截图、临时文件、帖子全文转录。
- 确认 README 和 `index.html` 不展示 `draft`、`status`、平台字段或 Linux.do 权限提示。
- 第一条收录是 `image-to-code-skill`，来源于 Linux.do 话题 `2314994` 和 GitHub 项目 `yuzhworkhard-wq/image-to-code`，内容基于原项目 README、SKILL.md 和用户提供的帖子原文综合提炼，但不保留原文存档。
- 原项目 README 和 SKILL.md 明确说明 `image-to-code-skill` 以 Codex skill 形式发布，但本索引读者视图按通用技能能力介绍，不展示平台字段。
- 第二条收录是 `guizang-ppt-skill`，来源于 Linux.do 话题 `2275626` 和 GitHub 项目 `op7418/guizang-ppt-skill`，内容基于 Linux.do 话题 JSON、原项目 README 与 SKILL.md 综合提炼，不保存帖子原文。
- `guizang-ppt-skill` 对外介绍重点应放在“单文件 HTML 横向翻页演示稿、电子杂志风、瑞士国际主义风、配图、截图风格化、多平台封面、版式自检”，不要写成普通 PPTX 模板。
- 第三条收录是 `awesome-ppt-skills`，来源于 Linux.do 话题 `2090997` 和 GitHub 项目 `stevenjinlong/awesome-ppt-skills`，内容基于 Linux.do 话题 JSON、原项目中文 README、`awesome-ppt`/`awesome-ppt-std`/`awesome-ppt-editable` 的 SKILL.md 综合提炼，不保存帖子原文。
- `awesome-ppt-skills` 对外介绍重点应放在“图片优先 PPTX、整页成图、标准版稳定输出、可编辑版实验性 ppt-master 重建”，并明确可编辑重建不是无损位图转矢量。
- 第四条收录是 `ppt-master`，来源于 Linux.do 话题 `1432693` 和 GitHub 项目 `hugohe3/ppt-master`，内容基于原项目 README、README_CN、`skills/ppt-master/SKILL.md` 和用户提供的来源链接综合提炼，不保存帖子原文。
- 用户提示 `ppt-master` 的 Linux.do 来源地址可能无法访问；展示层保留来源链接，详情页和结构化数据记录为可能需要登录或权限。
- `ppt-master` 对外介绍重点应放在“多格式文档输入、SVG 中间层、原生可编辑 PPTX、模板/品牌复用、实时预览、备注与动画导出”。它和 `awesome-ppt-skills` 的定位不同：`awesome-ppt-skills` 偏整页图片版 PPTX，`ppt-master` 偏原生可编辑 PPTX 工作流。
- 第五条收录是 `gpt-image2-ppt-skills`，来源于 Linux.do 话题 `2053515` 和 GitHub 项目 `JuneYaooo/gpt-image2-ppt-skills`，内容基于 Linux.do 话题、原项目 README、`SKILL.md`、实现逻辑和编辑能力说明综合提炼，不保存帖子原文。
- `gpt-image2-ppt-skills` 对外介绍重点应放在“gpt-image-2 整页视觉稿、图片型 PPTX、PPTX 模板克隆、自然语言指哪改哪、真实素材保真后贴、Markdown 编排和版本追踪”。它和 `awesome-ppt-skills` 都是图片优先路线，但本条更突出模板克隆、真实素材后贴和修改工作流；它和 `ppt-master` 的区别是后者偏原生可编辑 PPTX。
- 第六条收录是 `banana-slides`，来源于 Linux.do 话题 `1285413` 和 GitHub 项目 `Anionex/banana-slides`，内容基于用户提供的来源链接、原项目 README、`skills/banana-cli/SKILL.md` 和项目文档综合提炼，不保存帖子原文。
- `banana-slides` 对外介绍重点应放在“nano banana pro、Vibe PPT、一站式 Web 应用、素材工具箱、框选编辑、CLI、批量生成、PPTX/PDF/图片/讲解视频导出”。它和 `gpt-image2-ppt-skills` 都是图片生成驱动的 PPT 路线，但本条更像可部署产品；它和 `ppt-master` 的区别是后者偏原生可编辑 PPTX 工作流。
- Linux.do 话题 `1285413` 的 JSON 入口整理时不可公开访问；展示层保留来源链接，详情页和结构化数据记录为可能需要登录或权限。
- 第七条收录是 `thesis-defense-pptx-skill`，来源于 Linux.do 话题 `2091089` 和 GitHub 项目 `zouchenzhen/thesis-defense-pptx-skill`，内容基于 Linux.do 话题、原项目 README.zh-CN、README.en、`skills/thesis-defense-pptx/SKILL.md` 综合提炼，不保存帖子原文。
- `thesis-defense-pptx-skill` 对外介绍重点应放在“论文答辩专用、严格复用用户已有学校/学院/实验室 PPTX 模板、原生可编辑 PPTX、PowerPoint COM 复制模板页、逐页 PNG 导出、总览图检查、文字溢出检查和旧模板词扫描”。它和 `ppt-master` 都是原生可编辑 PPTX，但本条更窄且模板保真优先；它和图片型 PPT 技能的区别是输出可编辑对象而非整页图片。
- 第八条收录是 `GordenPPTSkill`，来源于 Linux.do 话题 `2278294` 和 GitHub 项目 `GordenSun/GordenPPTSkill`，内容基于 Linux.do 话题、原项目 README、`SKILL.md`、模板索引和工作流文档综合提炼，不保存帖子原文。
- `GordenPPTSkill` 对外介绍重点应放在“中文商务 PPTX 模板库、非破坏式文字替换、真实可编辑 PPTX、文本框容量/出框检测、同级标题字号一致、自动更新机制、用户自带模板模式”。它和 `thesis-defense-pptx-skill` 都重视模板保真，但本条更偏中文职场商务汇报和内置模板库；它和图片型 PPT 技能的区别是输出可编辑对象而非整页图片。
- `GordenPPTSkill` 的内置模板有非商业限制，详情页和结构化数据必须持续保留“仅个人学习研究，禁止商业使用或二次分发”的提醒。
- 第九条收录是 `karpathy-llm-wiki`，来源于 Linux.do 话题 `1945700` 的第 10 楼和 GitHub 项目 `Astro-Han/karpathy-llm-wiki`，内容基于 Linux.do 话题回复、原项目 README 与 `SKILL.md` 综合提炼，不保存帖子原文。
- `karpathy-llm-wiki` 对外介绍重点应放在“Karpathy LLM 学习资料、raw/ 原始资料、wiki/ Markdown 知识库、sources.yml、coverage.yml、带引用问答和 lint 健康检查”。它不是 PPT/图片/前端生成技能，应单独归类为知识管理。
- 第十条收录是 `graphify`，来源于 Linux.do 话题 `1907342` 和 GitHub 项目 `safishamsi/graphify`，内容基于用户提供的来源链接、原项目 README 与 `graphify/skill.md` 综合提炼，不保存帖子原文。
- `graphify` 对外介绍重点应放在“代码库/多模态资料转 Neo4j 知识图谱、GraphRAG、Gemini、图谱可视化、架构问答”。它和 `karpathy-llm-wiki` 都属于知识管理，但 `karpathy-llm-wiki` 是 Markdown wiki，`graphify` 是 Neo4j 图谱和 GraphRAG。
- 第十一条收录是 `wechat-article-reader`，推荐来源于 Linux.do 话题 `1956732` 的第 34 楼，GitHub 项目为 `jeffchan813/wechat-article-reader`，内容基于用户提供的推荐链接、原项目 README 与 `SKILL.md` 综合提炼，不保存帖子原文。
- `wechat-article-reader` 对外介绍重点应放在“微信公众号文章读取、curl 模拟浏览器请求、Python 正则提取 js_content、摘要/全文/图片链接/原始 HTML 输出、轻量无浏览器依赖”。它和 `karpathy-llm-wiki` 都涉及内容整理，但本条只负责单篇或批量微信公众号文章提取；它和 `graphify` 的区别是后者面向 Neo4j 图谱和 GraphRAG。
- 第十二条收录是 `GenericAgent`，来源于 Linux.do 话题 `1962519` 和 GitHub 项目 `lsdefine/GenericAgent`，内容基于 Linux.do 话题 JSON、GitHub 仓库元数据与原项目 README 综合提炼，不保存帖子原文。
- `GenericAgent` 必须作为“元技能与方法论”展示：它不包含普通意义上的可安装 skill 本体，而是主张 Agent 在对话和任务执行过程中自我生成、沉淀和迭代技能。对外介绍重点应放在“Self-evolving Agent、任务后反思沉淀 SOP/Skill、分层记忆、技能树、少量原子工具、低 token 开销、真实浏览器/本地系统控制”。
- 第十三条收录是 `deep-research`，来源于 Linux.do 话题 `2312664` 和 GitHub 项目 `hoolulu/deep-research`，内容基于 Linux.do 话题、原项目 README 与 `SKILL.md` 综合提炼，不保存帖子原文。
- `deep-research` 对外介绍重点应放在“/research 主题生成深度调研报告、19 种语言、quick/standard/deep 三档深度、在线 SearXNG + Scrapling 抓取、本地 MD/TXT/PDF/DOCX 资料、并行章节撰写、引用转换和质量检查”。它和 `graphify` 都处理资料，但本条产物是 Markdown 调研报告而不是 Neo4j 图谱；它和 `karpathy-llm-wiki` 的区别是偏主题报告生成，不是长期 wiki 维护。
- 第十四条收录是 `agents-progressive-disclosure`，来源于 Linux.do 话题 `2263095` 和 GitHub 项目 `Caph-dev/agents-progressive-disclosure`，内容基于 Linux.do 话题、原项目 README、`SKILL.md` 和 GitHub 元数据综合提炼，不保存帖子原文。
- `agents-progressive-disclosure` 必须作为“元技能与方法论 / Agent 指令治理”展示：它不生成业务代码或报告，而是把臃肿的 `AGENTS.md`、`CLAUDE.md`、`GEMINI.md` 等重构为精简入口文件和按需 docs/rules 路由。它和 `GenericAgent` 的区别是后者关注 Agent 自进化技能树，本条关注人为维护指令文件的上下文压缩、冲突扫描和规则保留验证。
- 第十五条收录是 `agent-cli-creator`，来源于 Linux.do 话题 `2269051` 和 GitHub 项目 `better-world-ai/agent-cli-creator`，内容基于推荐来源、原项目 README、README_EN 与 `SKILL.md` 综合提炼，不保存帖子原文。
- `agent-cli-creator` 必须作为“元技能与方法论 / Agent 工具链 / 网站 CLI 生成”展示：它通过 `kimi-webbridge` 复用真实 Chrome 登录态，先做站点考古，再为具体网站生成可复用 CLI，并可生成伴随 skill。它和 `agents-progressive-disclosure` 的区别是后者治理指令文件；和 `GenericAgent` 的区别是后者是完整自进化 Agent 框架；和 `wechat-article-reader` 的区别是后者是固定公众号读取工具，本条面向任意具体网站定制 CLI。
- 第十六至十八条收录是 `OpenCLI`、`CLI-Anything`、`bb-browser`，均来源于 Linux.do 话题 `2269051` 的同一组推荐。三者都应作为“元技能与方法论 / Agent 工具链 / CLI 化生态”展示，不要混入普通内容读取类。
- 第十九条收录是 `variant-clone-factory`，来源于 Linux.do 话题 `2642041` 和 GitHub 项目 `lulistart/variant-clone-factory`，内容基于 Linux.do 话题、原项目 README、DEPLOY.md、package.json 与 GitHub 元数据综合提炼，不保存帖子原文。
- `variant-clone-factory` 对外介绍重点应放在“Variant 共享链接、Capture/Classify/Codegen/Package ZIP/Visual QA、React 工程、Docker/Playwright、像素差异验收”。它和 `image-to-code-skill` 的区别是前者抓取 Variant 页面并生成 React 工程，后者以 UI 图片或设计稿为输入进行还原；当前只支持 React，未适配 Vue。
- 原项目是 Web 应用和 CLI，不提供可直接安装到 Codex 的 `SKILL.md`；展示和备注中需明确这一点。原仓库未声明许可证，读者视图需保留“仅处理有权使用的模板”的边界提示。
- 第二十至二十二条收录来自 Linux.do 话题 `2735151`：`gc-minimal-zine-poster-v0-3`、`photo-abstract-editorial` 与 `gathered-scenes-zine-skill`。同一帖子推荐了三个独立 GitHub 仓库，必须拆为三条收录，而不是合并成一个论坛帖条目。
- `gc-minimal-zine-poster-v0-3` 对外介绍重点应放在“高留白、一个清楚视觉事件、纸张/印刷质感、单一高纯度色彩、主题/文章/照片/参考图五种入口、照片保真分级、参考图系统化分析、质量门”。它与后两项的差异是：不要求照片输入，也承担可复用风格系统与 Prompt 编排；项目采用 MIT 许可证。
- `photo-abstract-editorial` 对外介绍重点应放在“原照片不改动、下方抽象记忆面板只由照片事实推导、平整象牙色底、诗意英文短标题、不是滤镜/重画/风格迁移”。它与 `gathered-scenes-zine-skill` 的差异是：不使用撕纸、纸纹或自由插画，且始终保留完整照片；许可证禁止未经授权的商业使用与商业分发。
- `gathered-scenes-zine-skill` 对外介绍两条来源帖推荐路线：实景拼贴 `scenes-gathered-zine-v1-3` 保留真实摄影并加入抽象插画场、色彩结构和撕纸边界；影像蒸馏 `scene-distillation-zine-v1-3` 不保留原照片，只从场景语义、情绪张力和视觉隐喻重新创作。仓库另有其他技能目录，本条不因此扩大收录范围。许可证仅限个人非商业使用，企业、客户、SaaS/API、付费服务和商业分发均需作者书面许可。
- 以上三项均依赖图片生成能力；`photo-abstract-editorial` 和 `gathered-scenes-zine-skill` 还要求上传照片。已按既有“收录技能同步安装本机 Codex”约定完成安装：`gc-minimal-zine-poster-v0-3`、`photo-abstract-editorial`、`scenes-gathered-zine-v1-3`、`scene-distillation-zine-v1-3` 的 canonical source 位于 `/Users/xlzhao/.cc-switch/skills/`，Codex 入口均为指向 canonical source 的软链接。
- `OpenCLI` 对外介绍重点应放在“网站/真实浏览器会话/Electron 应用/本地工具统一 CLI 枢纽、Browser Bridge、100+ 站点 adapter、opencli-browser、opencli-adapter-author、verify/trace/站点记忆”。它和 `agent-cli-creator` 的区别是：后者是生成某网站 CLI 的流程，OpenCLI 已提供完整运行时和官方 skills。
- `CLI-Anything` 对外介绍重点应放在“专业软件 Agent Native、CLI-Hub 市场、matrix 工作流、按 capability/preflight 最小化安装、cli-anything-* 独立包、JSON 输出”。它和 `OpenCLI` 的区别是：OpenCLI 偏网站/浏览器/桌面应用，CLI-Anything 偏专业软件和工作流矩阵。
- `bb-browser` 对外介绍重点应放在“你的浏览器就是 API、真实 Chrome 登录态、CLI + MCP、snapshot/click/fill/eval/fetch/network、bb-sites adapter”。它和 `OpenCLI` 都是真实浏览器路线，但 bb-browser 更偏轻量执行层，OpenCLI 更偏完整 CLI 枢纽与 adapter 生态。
- 仓库对外内容默认使用中文；底层 JSON 字段名保持英文，避免后续脚本维护成本升高。
- 后续优先在现有 JSON 结构上补字段和演进，不创建平行台账文件。
- 结构化数据中的 `skill_description` 用于保存可展示的原始 skill description，`display_label` 统一为 `description`，服务 README 和未来静态页扩展。
