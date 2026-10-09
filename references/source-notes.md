# 来源与取舍

研究日期：2026-10-07（Asia/Shanghai）。本技能以用户的课件要求为主要依据，独立撰写规则；其他技能与公开 GitHub 研究提供方法参考。下列记录用于维护与追溯，不要求制作时全部加载，也不构成外部技能依赖。

28/40 是优先视觉目标，信息密集页允许适度放宽并检查最终投影可读性；所有页面调用 ImageGen 或当前实际可用的 Images 2.5 整页直接生成图文。PPTX 为翻页容器，不默认原生可编辑。封面允许准确叠加 Logo 与姓名、日期等小字；内页普通标题、正文直接生成，不能全部原生覆盖来冒充整页生图。

## 方法来源与取舍

| 参考来源 | 采用的通用方法 | 边界与取舍 |
|---|---|---|
| `client-deck-imagegen-redraw` | 客户业务封面、精确素材保护、逐页内容锁、批量恢复、组装与渲染 | 保留整页生图路线；PPTX 容器不等于原生可编辑 |
| `design-ppt-visuals` | 一页一观点、视觉关系、逐页构图、风格一致性 | 提示词和规划不等于最终 PPTX；不继承强制 70/30 比例 |
| `baoyu-slide-deck` | 大纲、视觉规格、逐页提示、保存重试与合并 | 阅读分享的密度须按现场培训调整 |
| `slide-image-to-editable-ppt` | 图像拆解、精准源件分层、独立素材 | 原生重建不作为默认路线，元素包只按用户需求交付 |
| `guizang-ppt-skill` | 网格、留白、字体层级、章节节奏与演前检查 | 不继承强制深浅交替、限定 5 色板和标题字数限制；不移植 AGPL 模板代码 |
| `ai-tool-training-cases` | 真实操作截图、步骤标注、可复现任务与结果 | 使用当前可用的浏览器工具；不依赖来源技能的脚本 |
| `micro-course-delivery-sop` | 课程要求、教学目标、课件与讲稿同步、片段检查 | 不继承作者接单政策、固定字速、逐步批准或全程水印 |
| `minimax-skills/pptx-generator` | PPTX 组装、主题一致性、XML 盘点与 QA | 用于整页图片容器与必要精确合成；原生正文和小字号默认值不能覆盖整页生图要求 |
| Anthropic `pptx` | 文件结构、内容与实际渲染分别核验 | 专有许可；不复制文档、提示词或脚本到本技能 |
| `text-to-visual` | 内容分块、折行、线性图标、知识卡片 | 仅用于适合的配套材料，不承担课件制作主线 |
| `team-training-outline-designer` | 岗位行为目标、模块时长、示范/练习与成果判断 | 不继承固定练习比例 |
| `lark-slides` | 密集小字原生课件路线（未采用） | 不作为本技能默认制作方式 |

花叔相关方法的固定版本、来源与具体融合见 [花叔 Skill 的行业培训适配](alchain-huashu.md)。这些记录说明方法借鉴，不要求安装来源技能，也不证明其脚本在当前环境已通过完整验证。

## 依赖与执行边界

核心脚本仅依赖 `python-pptx` 与 `Pillow`，版本要求见仓库根目录的 `requirements.txt`。它们负责组装整页图片和讲师备注，不生成课件视觉。实际生图要求宿主环境提供可调用的 ImageGen；环境实际提供 Images 2.5 时可按用户要求使用。

每次制作检查当前工具、运行环境、账号与必要依赖。模块可导入不证明生图接口、浏览器登录、字体可移植或真实软件播放已通过。缺失时处理实际依赖，不无差别安装整套来源技能或工具。

各来源的固定访谈、阶段批准、交付扩张与原生编辑默认值不自动继承。真实 Logo、客户业务背景、金色手写封面、全套浅/深主基调及所有页直接生图沿用主技能规则。Logo、二维码、真实 UI 等精准对象允许保留源件合成，普通内页标题正文不能全部靠原生层替代生成。

ImageGen 以当前实际路由和参数执行；接口未明确返回或允许选择版本时，不能据名称就声称已成功调用 Images 2.5。依赖清单也不证明生图接口运行成功，每页须有真实生成结果与调用记录。

## GitHub 一手研究

以下为 2026-10-07 的公开 GitHub API 快照，属于历史记录。Stars（收藏数）只是关注指标；整仓收藏数不能归给其中单个课件技能，也不能证明制作质量或“全球最高”。

| 来源与归属 | Stars 快照及范围 | 融入的通用方法 | 许可/适用边界 |
|---|---:|---|---|
| Anthropic：[pptx](https://github.com/anthropics/skills/blob/main/skills/pptx/SKILL.md)；[API](https://api.github.com/repos/anthropics/skills) | 180,017，整个 `anthropics/skills` 集合 | 文件结构、内容与实际渲染分开检查，注意字体替换 | [子技能许可](https://github.com/anthropics/skills/blob/main/skills/pptx/LICENSE.txt) 为 Proprietary；仅说明通用思想，不复制材料 |
| JimLiu / 宝玉：[baoyu-slide-deck](https://github.com/JimLiu/baoyu-skills/blob/main/skills/baoyu-slide-deck/SKILL.md)；[API](https://api.github.com/repos/JimLiu/baoyu-skills) | 26,391，整个 `baoyu-skills` 集合 | 固定视觉规格、逐页来源与提示、只重做受影响页 | [整仓 MIT](https://github.com/JimLiu/baoyu-skills/blob/main/LICENSE)；整页图片 PPTX 不证明文字可编辑或字号通过 |
| op7418 / 歸藏：[guizang-ppt-skill](https://github.com/op7418/guizang-ppt-skill/blob/main/SKILL.md)；[API](https://api.github.com/repos/op7418/guizang-ppt-skill) | 27,357，专门的演示技能仓库 | 视觉体系、章节节奏、纪实照片和演前检查 | AGPL-3.0；本技能不移植模板或运行时代码；其网页产物不是原生 PPTX |
| K-Dense Inc.：[scientific-slides](https://github.com/K-Dense-AI/scientific-agent-skills/blob/main/skills/scientific-slides/SKILL.md)；[API](https://api.github.com/repos/K-Dense-AI/scientific-agent-skills) | 47,872，整个科研技能集合 | 根据受众与时间定页数，保留准确数据与引用，检查技术关系 | MIT 标注；不继承科研专用时间分配、论文数量或模型平台步骤 |
| siril9：[presentation-skill](https://github.com/siril9/presentation-skill/blob/main/SKILL.md)；[API](https://api.github.com/repos/siril9/presentation-skill) | 74，专门的 PowerPoint 技能仓库 | 可复建来源、论点与证据决定版式、事实数字与最终图表核对 | MIT；关注度低，不能称热门；默认标题 28 pt/正文 16 pt 不继承 |
| lgwanai：[ppt-skill](https://github.com/lgwanai/ppt-skill/blob/main/SKILL.md)；[API](https://api.github.com/repos/lgwanai/ppt-skill) | 17，专门的 PowerPoint 技能仓库 | 从参考课件提炼色板、字体、页型及章节节奏 | API 未声明仓库许可，不假定可复制；其风格一致度宣传未获独立核验 |

API 快照响应时间为 2026-10-07 15:13:08 UTC（北京时间 23:13:08）。归藏同日网页与 API 有不同收藏数，本表采用直接 API 的 27,357。最近仓库推送时间不等于单项技能更新时间或质量认证。本技能未复制上述外部原文或模板代码；若另行引入实现，先按具体文件许可处理归属与分发条件。

## 教学与视觉观察

对既有教学材料的观察提炼为以下通用规则，不把某份课件的页数、客户或章节数固化为后续模板：

- 客户标识、业务场景、主标题及讲师信息共同建立客户辨识；复用时更新身份与日期。
- 固定章节母版让阶段清楚，导航与行业素材保持一致；章节数量按课程目标决定。
- 岗位任务、简短调查及编号标注帮助理解与跟做；关键操作区域须放大。
- 实操案例呈现输入、处理、输出与复核链条，原材料与结果对照要能解释当前内容。
- 全套统一浅或深基调及标注体系；密集总览保留清楚主次，必要时减文或拆页。
- 生活化引入及时回到岗位资料，工具排名与效果数字保留统计日期、口径和测量依据。
- 小字截图和完整结果图可作总览；需要学员阅读的细节另做局部放大、重排或拆页。
- 生成工程图中的尺寸与技术信息不能直接作为已验证的设计依据。

PDF 导出缩放与图片内文字会影响字号读数，不能仅据 PDF 数值严格证明原 PPTX 达到 28/40 pt。整页生成文字以最终画幅的等效尺度及实际投影可读性核查；图片化 PPTX 不具备正文原生字号和逐项可编辑性的证明，PDF 也不能完整证明动画或现场播放效果。
