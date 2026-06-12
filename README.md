# Food Chemistry 写作助手 · Food Chemistry Writing Assistant

> 一站式《**Food Chemistry**》(Elsevier) 投稿写作助手 — 整合 *Guide for Authors*、*Submission
> Translator*、`academic-research-skills`(学术写作流水线) 与 `nature-skills`(Nature 风格写作/图表/审稿)。
>
> A one-stop writing assistant for submitting to **Food Chemistry** (Elsevier) — integrating the
> journal *Guide for Authors*, the *Submission Translator*, `academic-research-skills` (academic
> writing pipeline), and `nature-skills` (Nature-style writing / figures / review).

---

## 1. 这是什么 · What this is

**中文**：一个 Claude Code skill。围绕《Food Chemistry》的硬性投稿规范，把通用学术写作技巧与
Nature 风格写作/图表当作可调用的工具层，覆盖从零选题、文献综述、方法学设计、代码辅助、正文撰写、
修改润色、补充材料、投稿前合规审计、图表/图形摘要、参考文献规范，以及**定稿后**翻译。

**EN**: A Claude Code skill. It anchors on Food Chemistry's mandatory submission rules and treats
general academic-writing skills and Nature-style writing/figures as a callable tool layer. It covers
topic selection from scratch, literature review, methodology design, code assistance, drafting,
revision/polishing, supplementary materials, pre-submission compliance audit, figures / graphical
abstract, reference formatting, and translation **after the manuscript is finalized**.

---

## 2. 三条铁律 · Three hard rules

1. **优先级 · Priority** — 冲突时从高到低：
   `Guide for Authors > Food Chemistry 范文 > Submission Translator > academic-research-skills > nature-skills`。
   **Nature 风格绝不凌驾于 Food Chemistry 要求之上 · Nature style never overrides Food Chemistry.**
2. **先定稿后翻译 · Finalize first, translate later** — 默认全程中文；只有在收到明确的
   「翻译 / 定稿 / translate」指令后才输出英文。Chinese by default; English only after an explicit
   "translate / finalize" command.
3. **每改必交两份 markdown · Two mandatory reports per revision** — 每完成一篇文章的修改，必须额外用
   markdown 输出 **修改清单 (What Changed)** + **文章逻辑 (Article Logic)**。

---

## 3. 工作模式 · Modes

| 模式 · Mode | 用途 · Use | 触发示例 · Example prompt |
|---|---|---|
| **A. 从零开始 · From scratch** | 选题 / 文献综述 / 方法学 / 代码 / 正文 | 「就一个主题，帮我写 Food Chemistry 综述 / 设计方法学 / 写分析代码」 |
| **B. 修改润色 · Revise & polish** | 改写、提升逻辑与可读性、合规化 | 「帮我改这篇稿子」→ 自动出 修改清单 + 文章逻辑 |
| **C. 补充材料 · Supplementary** | 拆分 / 撰写 Supporting Information | 「帮我整理补充材料」→ 先问你：简单写 vs 堆工作量 / 中文 vs 英文 |
| **D. 投稿前审计 · Pre-submission audit** | 合规自查 / 模拟审稿 / 回复审稿人 | 「投稿前帮我做合规审计 / 模拟审稿」 |
| **E. 翻译定稿 · Translate** | 中文定稿后产出投稿级英文 | 中文定稿后说「翻译 / 出英文版」才会出英文 |
| **F. 图表 · Figures** | Figure / Graphical Abstract / 数据可视化 | 「画图 / 做图形摘要」（自动调用 nature-figure，格式服从 Food Chemistry） |

> 模式 C 开工前**必问两件事 · always asks first**：①简单写 vs 堆积工作量；②中文 vs 英文。

---

## 4. 怎么用 · How to use

**两种触发方式 · Two ways to trigger：**

1. **自然语言 · Natural language**（推荐 · recommended）— 说到触发词即自动调用。
   Just describe the task; trigger words activate it automatically.
   - 触发词 · Triggers: `Food Chemistry`、`食品化学投稿`、`写论文`、`文献综述`、`方法学`、`润色`、
     `修改文章`、`补充材料`、`Highlights`、`图形摘要`、`参考文献`、`投稿前审稿`、`定稿翻译` …
2. **斜杠命令 · Slash command** — 直接点名 · invoke by name：
   `/food-chemistry-writer`

**典型流程 · Typical flow：**

```
1. 中文写作 / 改稿  →  自动产出「修改清单 + 文章逻辑」
   Draft / revise in Chinese  →  auto "What Changed + Article Logic"
2. 投稿前  →  跑合规审计（Abstract ≤150词、Highlights、CRediT、AI 声明、Data Availability…）
   Before submission  →  compliance audit
3. 确认定稿 → 说「翻译」 → 产出投稿级英文 + 修改清单/逻辑
   Confirm final → say "translate" → submission-ready English + reports
```

---

## 5. 已安装的全部 skill · All installed skills

请提前下载`academic-research-skills`和`nature-skills`，并全部装在 `~/.claude/skills/`。
Please download `academic-research-skills`和`nature-skills` in advance, and all under `~/.claude/skills/`.

| 来源 · Source | Skills | Link |
|---|---|---|
| 本助手 · This assistant | `food-chemistry-writer` |
| academic-research-skills | `academic-paper`、`academic-paper-reviewer`、`academic-pipeline`、`deep-research` | https://github.com/Imbad0202/academic-research-skills |
| nature-skills | `nature-writing`、`nature-polishing`、`nature-figure`、`nature-citation`、`nature-reviewer`、`nature-response`、`nature-reader`、`nature-academic-search`、`nature-data`、`nature-paper2ppt` | https://github.com/Yuan1z0825/nature-skills |

`food-chemistry-writer` 会在需要时自动调度上述其它 skill（绘图→`nature-figure`，模拟审稿→
`nature-reviewer`/`academic-paper-reviewer`，查文献→`nature-academic-search` 等），你也可单独 `/` 调用。
The assistant auto-dispatches the others when needed; you can also call any of them directly with `/`.

---

## 6. 文件结构 · File structure

```
food-chemistry-writer/
├── SKILL.md                                       # 主指令文件 · main skill instructions
├── README.md                                      # 本文件 · this file
└── references/
    ├── Food_Chemistry_Guide_for_Authors.md        # 期刊硬性规范(最高权威) · journal rules (top authority)
    └── Food_Chemistry_Submission_Translator.md    # 翻译/定稿规则 · translation rules
```

> 安装位置 · Installed at: `~/.claude/skills/food-chemistry-writer/`

---

## 7. Food Chemistry 关键规范速查 · Key journal rules at a glance

| 项目 · Item | 要求 · Requirement |
|---|---|
| Abstract | ≤ **150 words**；可独立成段；尽量不引文献 · stand-alone, avoid references |
| Keywords | **1–7** 个，英文，尽量单词 · English, prefer single words |
| Highlights | **3–5** 条，每条 ≤ **85 字符**（含空格）· bullets, ≤85 chars each |
| Graphical Abstract | 531 × 1328 px (h×w)；TIFF/EPS/PDF/MS Office |
| 字数 · Length | Research/Analytical ≤ 8,000；Review ≤ 10,000；Short ≤ 3,000（且 ≤40 refs） |
| 图表 · Tables+Figures | 合计建议 ≤ **8** · ≤8 combined recommended |
| 引用 · Citations | 作者-年份，APA 第7版；字母序+时间序 · author–year (APA 7th) |
| 图件格式 · Figure formats | 矢量 EPS/PDF；位图 TIFF/JPG/PNG（≥300 dpi）。**不收 SVG** · SVG not accepted |
| 必备声明 · Statements | CRediT、Competing interests、Funding、Data availability (Option C)、AI 声明 |

> 完整规则以 `references/Food_Chemistry_Guide_for_Authors.md` 为准 · full rules govern.

---

## 8. 备注 · Notes
- 新开窗口若未识别新 skill，**重启 Claude Code** 即可刷新 · restart Claude Code to refresh.
- 本助手不替代人类判断，所有 AI 生成内容须经作者核验 · AI output must be verified by the author
  (per Food Chemistry generative-AI policy)。

---

*致谢 · Credits*：`academic-research-skills` (github.com/Imbad0202/academic-research-skills)、
`nature-skills` (github.com/Yuan1z0825/nature-skills)。
