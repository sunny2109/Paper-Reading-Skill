# Skills: Paper Reading & Research Analysis

[中文介绍](./README_zh.md)

## Repository Overview

This repository provides one reusable skill package for reading and critically analyzing computer science research papers.

Unlike a conventional summarization prompt, the skill turns paper reading into a question-driven analysis tree:

```text
problem
-> prior approaches and technical challenges
-> observation or insight
-> method and system design
-> claim-evidence mapping
-> limitations and failure cases
-> position in the literature tree
```

The workflow is applicable across artificial intelligence, theory and algorithms, systems, architecture, networking, databases, security, software engineering, programming languages, HCI, graphics, vision, robotics, and interdisciplinary computer science research.

## What the Skill Does

- Uses a three-pass reading workflow: screening, structured reading, and deep analysis.
- Builds a paper analysis tree instead of producing a chapter-by-chapter paraphrase.
- Explains each core module through motivation, mechanism, difference from prior work, and technical advantage.
- Separates paper facts, analytical inferences, and unverified research hypotheses.
- Maps major claims to experiments, proofs, measurements, user studies, or other evidence.
- Checks fairness, statistical validity, system cost, assumptions, reproducibility, and conclusion boundaries.
- Converts vague limitations into concrete failure cases and minimal stress tests.
- Places the paper in a literature tree and identifies milestone tasks and follow-up reading.
- Produces a minimal reproduction plan before recommending a full-scale reproduction.

## Repository Structure

- `SKILL.md`
  - Core workflow, reading-depth decisions, evidence rules, and output requirements.
- `references/paper-analysis-tree.md`
  - The reusable analysis tree covering problem, challenges, insight, method, evidence, limitations, and literature position.
- `references/domain-checklists.md`
  - Evidence-specific review checklists for machine learning, theory, systems, security, software engineering, HCI, vision, robotics, datasets, and benchmarks.
- `references/report-template.md`
  - A structured report template for quick screening, standard reading, deep analysis, reproduction, and literature-tree updates.
- `agents/openai.yaml`
  - Agent-facing display metadata and the default invocation prompt.

## Typical Use Cases

- Quickly deciding whether a paper deserves further reading.
- Producing a structured paper note with page, figure, table, formula, or code references.
- Understanding why a method was designed, not just what components it contains.
- Auditing whether experiments or proofs support the paper's main claims.
- Comparing a paper with its closest prior work and competing technical routes.
- Identifying hidden assumptions, unfair comparisons, failure cases, and missing evidence.
- Designing a minimal reproduction or stress test.
- Updating a literature review, literature tree, or research roadmap.
- Generating concrete, testable follow-up research hypotheses.

## Reading Workflow

### Pass 1: Screening

Read the title, abstract, conclusion, overview figure, and main result table when necessary. Rate relevance, potential contribution, evidence credibility, and the value of further reading.

### Pass 2: Paper Analysis Tree

Read the full paper and answer six core questions:

1. What problem, setting, assumptions, and constraints does the paper define?
2. Which prior approaches exist, and what technical limitations remain?
3. What observation or insight motivates the proposed method?
4. Which evidence supports each major claim?
5. Where can the method fail, and what remains unverified?
6. How can the paper be summarized as problem, challenge, insight, method, evidence, and boundary?

### Pass 3: Mechanism, System, and Reproduction

Reconstruct the end-to-end mechanism, inspect formulas or code when necessary, analyze component interactions and error propagation, design counterfactual tests, and create a minimal reproduction plan.

## Installation

Assume you are in the repository root.

### 1. Codex

Copy the skill files into `$CODEX_HOME/skills/paper-reading-research/`:

```bash
mkdir -p "$CODEX_HOME/skills/paper-reading-research"
cp -R SKILL.md agents references "$CODEX_HOME/skills/paper-reading-research/"
```

Usage examples:

```text
Use $paper-reading-research to analyze this paper and build its paper analysis tree.
```

```text
Use $paper-reading-research to perform only the first-pass screening of this paper.
```

```text
Use $paper-reading-research to audit the claim-evidence alignment and design a minimal reproduction.
```

### 2. CC (Claude Code)

Use either a global or project-level installation.

Global:

```bash
mkdir -p "$HOME/.claude/skills/paper-reading-research"
cp -R SKILL.md agents references "$HOME/.claude/skills/paper-reading-research/"
```

Project-level:

```bash
mkdir -p .claude/skills/paper-reading-research
cp -R SKILL.md agents references .claude/skills/paper-reading-research/
```

In prompts, explicitly request the skill, for example:

```text
Please use the paper-reading-research skill to analyze this paper.
```

### 3. Gemini

Copy the skill files into your Gemini skills directory:

```bash
mkdir -p "$HOME/.gemini/skills/paper-reading-research"
cp -R SKILL.md agents references "$HOME/.gemini/skills/paper-reading-research/"
```

Then request a concrete task, such as building the paper analysis tree, checking experimental evidence, or proposing a minimal reproduction.

Support for skill discovery and metadata may vary between clients. When automatic discovery is unavailable, explicitly reference the skill name in the prompt.

## Output Principles

The skill distinguishes four kinds of statements:

- **Paper fact:** directly supported by the paper, supplementary material, code, or artifact.
- **Analytical inference:** a reasoned interpretation derived from the available evidence.
- **Research hypothesis:** a proposed extension that has not yet been validated.
- **Missing information:** information that the available materials do not report.

Major judgments should be traceable to a page, section, figure, table, equation, code location, or experimental setting.

## Acknowledgments

- [李沐]如何读论文: <https://www.bilibili.com/video/BV1H44y1t75x/?vd_source=b861d930c8c876c6be0f572b2d809d61>

- [彭思达]如何有效地读论文：<https://pengsida.notion.site/d192db870bc64436ae4a4a590b36772a>