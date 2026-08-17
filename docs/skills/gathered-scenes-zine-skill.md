# gathered-scenes-zine-skill

## 快速判断

`gathered-scenes-zine-skill` 是一组从照片出发的纸刊创作技能，提供两条路线：`scenes-gathered-zine-v1-3` 把真实照片保留在作品中，配合抽象插画、色彩结构与撕纸边界；`scene-distillation-zine-v1-3` 则只提取照片的场景关系和情绪，重新创作独立插画，不在成品中保留原照片。

## 适合场景

- 你想把旅行、街拍或日常照片做成有纸张触感的拼贴海报。
- 你希望保留真实人物、空间关系或现场身份，同时压缩枝叶、人群和纹理等复杂细节。
- 你想从照片中提炼“靠近与错过”等情绪命题，做一张不依赖原图的编辑插画。

## 前置要求

- 一张可上传的照片。
- 具备图片生成能力的运行环境。
- 仅限个人非商业学习、研究或创作；商业使用须取得作者书面许可。

## 输入与输出

输入：

- 一张照片。
- 可选的保留关系、文字语言、情绪方向、比例或“单色块模式”要求。

输出：

- 实景拼贴：保留摄影现场、抽象插画场、单一高纯度色彩和可见撕纸纤维边界的成图。
- 影像蒸馏：不保留照片本身的独立纸刊插画，以及简短中文创作说明和艺术指导说明。

## 核心特色

- 两条路径清晰分工：实景拼贴保留现场，影像蒸馏保留语义与情绪。
- 先读场景，再生成：强调主体、空间关系、方向、视觉重心、原生色彩和最小语义线索。
- 复杂细节会被压缩成少量纸上形状、色块和方向手势，保留关系而非复制所有细节。
- 高纯度色彩不是点缀，而是承担视觉重心、方向或画面平衡的结构角色。

## 和相近技能的差异

- 相比 [photo-abstract-editorial](photo-abstract-editorial.md)，本项目可以选择不保留原照片，并采用更自由的纸张、撕纸、印刷感和插画语法；前者始终保留完整照片，抽象面板也更克制。
- 相比 [gc-minimal-zine-poster](gc-minimal-zine-poster.md)，本项目的核心输入是照片，重点是从实际场景提取关系；前者还可以从文章、主题和参考图系统开始创作。

## 工作流程

1. 阅读照片，建立主体、空间关系、方向、视觉重心、色彩和情绪的场景卡片。
2. 选择实景拼贴或影像蒸馏。
3. 实景拼贴保留真实摄影，用插画场、撕纸边界和色彩结构延展画面。
4. 影像蒸馏将照片转为命题、张力和视觉隐喻，重新组织纸上作品。
5. 按子技能规则输出成图及简短创作说明。

## 当前限制

- 两条路径都需要用户提供照片，且图片模型的理解能力会影响材质、边界和抽象关系。
- 实景拼贴以真实场景与空间关系为优先，影像蒸馏则不保证保留原图构图或细节。
- 许可证仅允许个人非商业使用；不得用于企业、客户项目、付费服务、SaaS/API 或商业分发。

## 链接

- 项目仓库：<https://github.com/Zeejay0/gathered-scenes-zine-skill>
- 项目说明：<https://github.com/Zeejay0/gathered-scenes-zine-skill/blob/main/README.md>
- 实景拼贴 Skill：<https://github.com/Zeejay0/gathered-scenes-zine-skill/blob/main/skills/scenes-gathered-zine-v1-3/SKILL.md>
- 影像蒸馏 Skill：<https://github.com/Zeejay0/gathered-scenes-zine-skill/blob/main/skills/scene-distillation-zine-v1-3/SKILL.md>
- 许可证：<https://github.com/Zeejay0/gathered-scenes-zine-skill/blob/main/LICENSE>
- 收录来源：<https://linux.do/t/topic/2735151>

## 备注

本条只覆盖来源帖子推荐的实景拼贴与影像蒸馏两条路径。项目许可证为个人非商业许可；论坛帖子原文不作为仓库存档保留。
