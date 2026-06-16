这里是为您完整更新后的 `README.md`，我已经新增了 **第 7 节：数据与代码可用性声明示例 (Data Availability Examples)**。

在这些示例中，我结合了现代数字化科研的常见场景（如使用 Python/Pandas 处理重度数据，以及在 GitHub 和 Hugging Face 上托管代码、模型与数据集），并展示了如何优雅且合规地将其嵌入到《Food Chemistry》的正文和参考文献中。

您可以直接复制以下完整内容替换您的 `README.md` 文件：

```markdown
# Food Chemistry 写作助手 · Food Chemistry Writing Assistant

> 面向《**Food Chemistry**》(Elsevier) 的一站式投稿写作助手与端到端学术生产流水线。
>
> A one-stop writing assistant and end-to-end academic production pipeline for submitting to **Food Chemistry** (Elsevier).

---

## 1. 核心定位 · What this is

**中文**：一个强大的 Claude Code skill (v2.0)。它严格锚定《Food Chemistry》的硬性投稿规范，并将通用学术写作技巧 (`academic-research-skills`) 与 Nature 风格排版/作图 (`nature-skills`) 作为底层的工具层。覆盖从前期选题、使用 Python/Pandas 进行数据分析与代码辅助、方法学设计、正文起草、润色修改、基于 GitHub/Hugging Face 等平台的数据资产合规托管，直到**定稿后**的专业级学术翻译。

**EN**: An integrated Claude Code skill (v2.0). It enforces Food Chemistry's strict submission rules while leveraging `academic-research-skills` and `nature-skills` as a robust tool layer. It covers everything from topic selection, data analysis using Python/Pandas, drafting, and polishing, to research asset management via platforms like GitHub or Hugging Face for compliance, and final submission-ready translation **after the manuscript is finalized**.

---

## 2. 核心铁律 · Core Rules

1. **绝对优先级 · Priority**：发生冲突时，严格遵循 `Guide for Authors > 参考范文 > Submission Translator > academic-research-skills > nature-skills`。**（注：Nature 风格除作图外，绝不凌驾于本刊规范之上）**。
2. **先定稿后翻译 · Finalize first, translate later**：默认全程中文交流与起草；仅在接收到明确的「翻译 / 定稿 / translate」指令后，才调用翻译引擎输出符合 APA 7th (作者-年份) 规范的投稿级英文。
3. **强制输出交付物 · Mandatory Reports**：每完成一次针对文章的修改，系统将强制输出两份 Markdown 报告：**修改清单 (What Changed)** 与 **文章逻辑 (Article Logic)**。
4. **逻辑至上 · Logic First**：行文逻辑、数据支撑主张的严密性以及各部分之间的衔接，优先级高于一切辞藻修饰。

---

## 3. 工作模式 · Modes

| 模式 · Mode | 适用场景 · Scenarios | 触发示例 · Example prompt |
|---|---|---|
| **A. 从零开始 · From scratch** | 选题定位 / 文献综述 / 方法学设计 / 分析代码辅助 | 「帮我评估这个选题是否契合 Aims & Scope，并设计统计分析的代码框架」 |
| **B. 修改润色 · Revise & polish** | 优化逻辑、精简去重、去 AI 腔、合规化改造 | 「帮我改这篇初稿」→ *自动产出 修改清单 + 文章逻辑* |
| **C. 补充材料 · Supplementary** | 剥离冗长方法、管理大型组图与补充数据集 | 「帮我把正文里的多余图表整理成补充材料」 |
| **D. 投稿前审计 · Pre-submission**| 合规自查 (Highlights/CRediT/Data Option C) / 模拟审稿 | 「投稿前帮我做一次全面的合规审计和模拟审稿」 |
| **E. 翻译定稿 · Translate** | 中文逻辑确认无误，生成最终投稿版本 | 「正文已定稿，请按本刊要求输出最终英文版」 |
| **F. 图表与数据 · Figures & Data**| 生成 Graphical Abstract / 绘制高分辨矢量图表 | 「根据这组数据画图，并生成图形摘要的文本描述」 |

> ⚠️ **提示**：在执行 **C 模式 (补充材料)** 前，助手会主动向您确认两件事：① 是“仅满足合规的极简版”还是“详尽的工作量堆积版”；② 使用中文还是英文撰写。

---

## 4. 如何使用 · How to use

**方式一：自然语言对话 · Natural language**（推荐）
在对话中提及以下触发词即可自动激活技能：
`Food Chemistry`、`食品化学投稿`、`方法学设计`、`代码辅助`、`润色`、`补充材料`、`Highlights`、`图形摘要`、`投稿前审稿`、`定稿翻译`...

**方式二：斜杠命令 · Slash command**
直接在终端呼出：`/food-chemistry-writer`

**标准工作流建议 · Standard Workflow：**
```text
1. 前期处理 → 使用代码清洗数据，起草中文核心方法与结果
2. 逻辑迭代 → 循环修改与润色，每次自动获取「修改清单 + 文章逻辑」
3. 资产合规 → 梳理代码与数据并托管至外部仓库，满足 Option C 要求
4. 合规审计 → 跑完所有非学术维度的审查 (CRediT、字数、声明)
5. 翻译定稿 → 下达翻译指令，获取最终英文版与图表附件

```

---

## 5. 依赖与环境 · Dependencies

为了使流水线完整运转，请务必提前下载以下依赖，并将它们统一放置于 `~/.claude/skills/` 目录下：

| 来源 · Source | 所属 Skills 列表 | 仓库地址 · Link |
| --- | --- | --- |
| **本助手** | `food-chemistry-writer` | - |
| **学术核心** | `academic-paper`, `academic-reviewer`, `academic-pipeline`, `deep-research` | [academic-research-skills](https://github.com/Imbad0202/academic-research-skills) |
| **图表与排版** | `nature-writing`, `nature-figure`, `nature-citation`, `nature-data` 等 | [nature-skills](https://github.com/Yuan1z0825/nature-skills) |

*注：本助手会在需要时自动静默调度上述依赖（如：绘制组图时调度 `nature-figure`，模拟审稿时调度 `academic-paper-reviewer`）。*

---

## 6. Food Chemistry 关键规范速查 · Quick Reference

| 检查项 · Item | 硬性要求 · Requirement |
| --- | --- |
| **Abstract** | ≤ **150 words**；可独立成段；尽量不引文献 |
| **Keywords** | **1–7** 个；英文；尽量使用单词而非词组 |
| **Highlights** | 单独提交；**3–5** 条 bullets；每条 ≤ **85 字符**（含空格） |
| **Graphical Abstract** | 尺寸 531 × 1328 px (h×w) 或等比；PNG/PDF/MS Office 格式 |
| **图表合计** | 建议总数 ≤ **8**（多余内容务必移至 Supplementary） |
| **参考文献** | 采用**作者-年份**制 (APA 7th)；字母序 + 时间序 |
| **图件格式** | 矢量推荐 PDF；位图推荐 PNG (≥300 dpi)。**明确拒收 SVG 格式** |
| **数据与代码** | 适用 Data Availability Option C（要求提供外部仓库访问链接） |

---

## 7. 数据与代码可用性声明示例 (Data Availability Examples)

《Food Chemistry》要求适用 **Option C**，即建议作者将相关数据集和分析代码托管在外部仓库中，并在正文的 `Data availability` 章节以及参考文献列表中进行声明和引用。

下面是如何在手稿中优雅集成这些信息的模板范例：

### 示例 A：托管 Python/Pandas 分析脚本至 GitHub

如果在研究中使用了自定义脚本进行数据处理和统计分析：

**正文声明 (Data availability 章节)：**

> The Python and Pandas scripts utilized for marine product data manipulation and heavy statistical analyses in this study are open-source and hosted on GitHub. The repository can be accessed at https://github.com/YourUsername/Marine-Food-Chem-Analysis (Zheng, 2026).

**文末参考文献 (References 章节)：**

> Zheng, J. (2026). *Marine-Food-Chem-Analysis: Python scripts for metabolic profiling of marine resources*. GitHub. https://github.com/YourUsername/Marine-Food-Chem-Analysis

### 示例 B：托管深度学习模型/组学数据至 Hugging Face 或 Mendeley Data

如果在研究中训练了辅助判别的 AI 模型或包含大量的原始数据集：

**正文声明 (Data availability 章节)：**

> The raw metabolomic datasets and the trained prediction models have been deposited in the Hugging Face repository and Mendeley Data, respectively, and are publicly available (Zheng et al., 2026a; Zheng et al., 2026b).

**文末参考文献 (References 章节)：**

> `[dataset]` Zheng, J., et al. (2026a). *Raw metabolomic profiles of marine-derived polysaccharides (Version 1)*. Mendeley Data. https://doi.org/10.17632/xxxxxxx.1
> Zheng, J., et al. (2026b). *Pre-trained models for food authenticity verification*. Hugging Face. https://huggingface.co/YourUsername/Food-Authenticity-Model

---

## 8. 备注 · Notes

* 新开窗口若未识别新 skill，**重启 Claude Code** 即可刷新 · restart Claude Code to refresh.
* 本助手不替代人类判断，所有 AI 生成内容须经作者核验 · AI output must be verified by the author
(per Food Chemistry generative-AI policy)。

---

*致谢 · Credits*：

* `academic-research-skills` (github.com/Imbad0202/academic-research-skills)
* `nature-skills` (github.com/Yuan1z0825/nature-skills)

```

```
