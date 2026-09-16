# Skills：论文阅读与科研分析

[English](./README.md)


## 仓库简介

本仓库提供一个用于阅读和批判性分析计算机学科论文的可复用 Skill。

它不是普通的论文摘要提示词，而是将论文阅读转化为一棵问题驱动的解析树：

```text
研究问题
-> 前作路线与技术挑战
-> 核心观察或洞见
-> 方法与系统设计
-> 主张—证据对应关系
-> 局限与失败场景
-> 在 literature tree 中的位置
```

该流程适用于人工智能、理论与算法、系统、体系结构、网络、数据库、安全、软件工程、程序语言、HCI、图形学、计算机视觉、机器人及其他计算机交叉研究方向。

## Skill 能做什么

- 使用三遍式流程完成论文筛选、结构化通读和深度分析。
- 构建论文解析树，而不是按章节机械复述。
- 从动机、机制、前作差异和技术优势四个维度解释核心模块。
- 区分论文事实、分析推断和未经验证的研究假设。
- 将主要主张映射到实验、证明、系统测量、用户研究或其他证据。
- 检查比较公平性、统计有效性、系统成本、关键假设、复现性和结论边界。
- 将抽象 limitation 转化为具体 failure cases 和最小压力测试。
- 判断论文在 literature tree 中的位置、对应的 milestone task 和后续阅读方向。
- 在建议完整复现前，先设计低成本的最小复现方案。

## 仓库结构

- `SKILL.md`
  - 核心阅读流程、阅读深度决策、证据规则和输出要求。
- `references/paper-analysis-tree.md`
  - 覆盖问题、挑战、洞见、方法、证据、局限和领域位置的论文解析树。
- `references/domain-checklists.md`
  - 面向机器学习、理论、系统、安全、软件工程、HCI、视觉、机器人、数据集和基准的证据类型检查表。
- `references/report-template.md`
  - 用于快速筛选、标准阅读、深度分析、复现规划和 literature tree 更新的报告模板。
- `agents/openai.yaml`
  - Agent 展示信息和默认调用提示。

## 典型使用场景

- 快速判断一篇论文是否值得继续阅读。
- 生成带页码、图表、公式或代码定位的结构化论文笔记。
- 理解作者为什么这样设计，而不仅是知道论文包含哪些模块。
- 审查实验或证明是否真正支持论文的核心主张。
- 比较论文与最近前作、里程碑论文及竞争路线的关系。
- 发现隐含假设、不公平比较、失败场景和缺失证据。
- 设计最小复现或压力测试。
- 更新文献综述、literature tree 或研究路线图。
- 形成具体且可验证的后续研究假设。

## 阅读流程

### 第一遍：快速筛选

阅读标题、摘要和结论；必要时查看方法总览图和实验主表。评估相关性、潜在贡献、证据可信度和继续阅读价值。

### 第二遍：论文解析树

完整通读论文并回答六个核心问题：

1. 论文定义了什么问题、场景、假设和约束？
2. 之前有哪些技术路线，它们为什么仍然受限？
3. 作者发现了什么观察或洞见，由此提出了什么方法？
4. 哪些证据分别支撑论文的主要主张？
5. 方法可能在哪里失败，还有哪些关键结论没有验证？
6. 如何用“问题—挑战—洞见—方法—证据—边界”总结论文？

### 第三遍：机制、系统与复现

重建端到端机制，必要时阅读公式或代码，分析模块交互和错误传播，设计反事实测试，并形成最小复现方案。

## 安装

以下命令假设当前目录为仓库根目录。

### 1. Codex

将 Skill 文件复制到 `$CODEX_HOME/skills/paper-reading-research/`：

```bash
mkdir -p "$CODEX_HOME/skills/paper-reading-research"
cp -R SKILL.md agents references "$CODEX_HOME/skills/paper-reading-research/"
```

使用示例：

```text
请使用 $paper-reading-research 分析这篇论文，并构建论文解析树。
```

```text
请使用 $paper-reading-research 只对这篇论文进行第一遍快速筛选。
```

```text
请使用 $paper-reading-research 检查论文的主张—证据关系，并设计最小复现方案。
```

### 2. CC（Claude Code）

可以全局安装，也可以仅在当前项目中安装。

全局安装：

```bash
mkdir -p "$HOME/.claude/skills/paper-reading-research"
cp -R SKILL.md agents references "$HOME/.claude/skills/paper-reading-research/"
```

项目级安装：

```bash
mkdir -p .claude/skills/paper-reading-research
cp -R SKILL.md agents references .claude/skills/paper-reading-research/
```

在提示词中明确要求使用该 Skill，例如：

```text
请使用 paper-reading-research skill 分析这篇论文。
```

### 3. Gemini

将 Skill 文件复制到 Gemini 的 skills 目录：

```bash
mkdir -p "$HOME/.gemini/skills/paper-reading-research"
cp -R SKILL.md agents references "$HOME/.gemini/skills/paper-reading-research/"
```

随后提出具体任务，例如构建论文解析树、审查实验证据或设计最小复现。

不同客户端对 Skill 自动发现和元数据的支持可能不同；无法自动发现时，请在提示词中明确指定 Skill 名称。

## 输出原则

Skill 会区分四类内容：

- **论文事实**：由论文、补充材料、代码或 artifact 直接支持。
- **分析推断**：基于现有证据得到的解释。
- **研究假设**：尚未经过验证的延伸方案。
- **缺失信息**：当前材料没有报告的内容。

重要判断应尽量定位到页码、章节、图、表、公式、代码位置或实验设置。

## 致谢

- [李沐] 如何读论文: <https://www.bilibili.com/video/BV1H44y1t75x/?vd_source=b861d930c8c876c6be0f572b2d809d61>
- [彭思达] 如何有效地读论文：<https://pengsida.notion.site/d192db870bc64436ae4a4a590b36772a>

