# Ultimate 行业培训课件 Skill

米尼的中文客户培训课件制作技能：从课程目标、客户品牌与行业案例组织内容，逐页调用 ImageGen 生成完整页面，核验后组装为图片型 PPTX 与 PDF。

## 能做什么

- 设计课程结构、岗位实操、课堂互动与讲师备注。
- 制作客户品牌封面：真实 Logo、客户业务场景、金色中文手写主标题、讲师姓名与培训日期。
- 逐页生成完整图文，保持全套浅色或深色基调；正文 28 pt、标题 40 pt 为优先视觉目标，密集页按最终可读性调整。
- 从旧课件改版，核对中文、事实、数据关系、页序与行业适配。
- 把已核验的整页图片和备注组装为 PPTX 与 PDF。

默认讲师姓名为“米尼”。客户名称、Logo、培训日期及业务事实应由本次资料确定。具体规范见 [SKILL.md](SKILL.md)。

## 安装到 Codex

下载或克隆本仓库后，在仓库根目录执行：

```bash
mkdir -p "$HOME/.codex/skills/ultimate-courseware"
cp -R SKILL.md agents references scripts requirements.txt README.md "$HOME/.codex/skills/ultimate-courseware/"
```

在 Codex 中重新开始会话，并调用：

```text
请使用 $ultimate-courseware，为我的客户制作中文培训课件。
```

同时提供课程主题、客户资料、学员岗位、培训时长，以及需要保留的旧稿或素材；已有信息足够时，技能会直接推进。

## 环境与输出

逐页生图需要宿主环境提供实际可调用的 **ImageGen** 工具。安装技能文件不会开通生图能力。若当前环境确实提供 Images 2.5，也可按用户要求使用；工具没有版本选择或返回信息时，只报告实际使用 ImageGen。

默认所有页面直接生成完整图文。真实 Logo、二维码、真实界面与必须准确的源对象允许保留原件并精确合成。生成文字和数据仍须逐页核对。

**PPTX 每页包含一张整页图片，图内文字不可逐项编辑；PDF 也是图片版。** 组装脚本不生成图片，也不代替内容和视觉验收。

## 图片组装

脚本使用 Python 3.8 或更高版本，以及 `python-pptx`、`Pillow`。建议在独立环境中安装依赖：

```bash
python3 -m venv .venv
.venv/bin/python -m pip install -r requirements.txt
```

准备已核验的页面图片，并创建 `manifest.json`；图片路径相对于清单所在目录：

```json
{
  "title": "客户培训课件",
  "slides": [
    {"image": "pages/001.png", "title": "课程封面", "notes": "讲师备注"},
    {"image": "pages/002.png", "title": "岗位任务"}
  ]
}
```

在仓库根目录运行：

```bash
.venv/bin/python scripts/assemble_image_deck.py manifest.json \
  --pptx final.pptx --pdf final.pdf
```

默认画幅为 16:9；可在清单中添加 `canvas`，用 `width_inches` 与 `height_inches` 指定画幅。图片比例偏差超过 0.5% 会报错，已有输出文件不会被覆盖。运行前须将清单与课程大纲逐项核对，运行后打开成品检查页数、页序、图片与备注。

## 目录

| 文件 | 用途 |
|---|---|
| [SKILL.md](SKILL.md) | 主技能入口与完整制作规范 |
| [agents/openai.yaml](agents/openai.yaml) | Codex 的技能显示信息与默认调用提示 |
| [scripts/assemble_image_deck.py](scripts/assemble_image_deck.py) | 整页图片与备注组装为 PPTX/PDF |
| [references/visual-and-teaching.md](references/visual-and-teaching.md) | 封面、页型、提示词与岗位教学设计 |
| [references/production-and-qa.md](references/production-and-qa.md) | 实际生图、可读性、内容核验与交付检查 |
| [references/alchain-huashu.md](references/alchain-huashu.md) | 花叔相关方法的行业培训适配 |
| [references/source-notes.md](references/source-notes.md) | 方法来源、研究日期与许可证边界 |
| [requirements.txt](requirements.txt) | 图片组装所需 Python 库 |

本仓库不包含客户课件、客户 Logo、账号凭证或生图密钥。参考来源用于说明方法，不要求安装其他课件技能。本仓库未指定开源许可证。
