[中文](./README.md) · **English**

# Investment Research Skills

#### Agent Skills for investment research workflows

[![License](https://img.shields.io/badge/License-MIT-3B82F6?style=for-the-badge)](./LICENSE)
[![Skills](https://img.shields.io/badge/Skills-5-10B981?style=for-the-badge)](#-skills)
[![AgentSkills](https://img.shields.io/badge/AgentSkills-Standard-8B5CF6?style=for-the-badge)](https://agentskills.io)

![Claude Code](https://img.shields.io/badge/Claude_Code-Skill-D97706?style=flat-square&logo=anthropic&logoColor=white)
![Codex](https://img.shields.io/badge/Codex-Skill-10B981?style=flat-square&logo=openai&logoColor=white)
![OpenCode](https://img.shields.io/badge/OpenCode-Skill-3B82F6?style=flat-square)

This repository collects reusable Agent Skills for investment research. Each skill is a standalone structured instruction set that follows the [Agent Skills](https://agentskills.io) open format and can be loaded by clients that support `SKILL.md`.

The current skills are Chinese-first and designed for company research, industry entry-barrier analysis, moat testing, competitor attack simulation, and financial/business-model validation.

---

## Index

| Name | One-liner | Entry |
| --- | --- | --- |
| [**company-moat-research**](#-company-moat-research) | Analyze company moats and industry entry barriers from new entrant, industry researcher, and long-term investor perspectives | [SKILL.md](./company-moat-research/SKILL.md) |
| [**valuation-expectation-check**](#-valuation-expectation-check) | Check the market expectations, valuation risk, and validation metrics implied by the current stock price | [SKILL.md](./valuation-expectation-check/SKILL.md) |
| [**integrated-equity-research-report**](#-integrated-equity-research-report) | Merge moat research, valuation checks, and other investment materials into a standardized Markdown research report | [SKILL.md](./integrated-equity-research-report/SKILL.md) |
| [**equity-research-pipeline**](#-equity-research-pipeline) | One command to run moat research, valuation check, and report generation end-to-end | [SKILL.md](./equity-research-pipeline/SKILL.md) |
| [**equity-comparison-advisor**](#-equity-comparison-advisor) | Compare multiple company reports, rank candidates, and build a decision framework | [SKILL.md](./equity-comparison-advisor/SKILL.md) |

---

## Install

In an agent that supports Skills, ask the agent to install the skill directory:

```text
Install this skill: https://github.com/vampire-locker/investment-research-skills/tree/main/company-moat-research
```

Manual install for Codex. Install one skill:

```bash
git clone git@github.com:vampire-locker/investment-research-skills.git
mkdir -p ~/.codex/skills
cp -R investment-research-skills/company-moat-research ~/.codex/skills/
```

Install all skills:

```bash
git clone git@github.com:vampire-locker/investment-research-skills.git
mkdir -p ~/.codex/skills
cp -R investment-research-skills/company-moat-research ~/.codex/skills/
cp -R investment-research-skills/valuation-expectation-check ~/.codex/skills/
cp -R investment-research-skills/integrated-equity-research-report ~/.codex/skills/
cp -R investment-research-skills/equity-research-pipeline ~/.codex/skills/
cp -R investment-research-skills/equity-comparison-advisor ~/.codex/skills/
```

For Claude Code, OpenCode, and other clients, import the desired skill directory according to the client's current skill workflow.

---

## Workflow

These skills can be used independently or as a complete research chain: analyze the moat first, then check the expectations implied by the current stock price, and finally turn the work into a standardized Markdown report. You can also use `equity-research-pipeline` to run the entire flow in one command. After generating reports for multiple companies, use `equity-comparison-advisor` to compare, rank, and frame portfolio decisions.

```mermaid
flowchart TD
    A["company-moat-research<br/>Company moat research"] --> B["valuation-expectation-check<br/>Valuation expectation check"]
    A --> C["integrated-equity-research-report<br/>Integrated equity research report"]
    B --> C
    P["equity-research-pipeline<br/>End-to-end equity research"] --> A
    P --> G["equity-comparison-advisor<br/>Equity comparison advisor"]
    C --> G

    A -.-> D["Business boundary / Entry barriers / Moat / Business model"]
    B -.-> E["Current valuation / Implied expectations / Re-rating and de-rating conditions"]
    C -.-> F["Standardized Markdown research report"]
    G -.-> H["Comparison / Ranking / Risk-reward matrix / Allocation framework"]
```

---

## ✨ Skills

### company-moat-research

> *"If I were a well-funded and highly capable new entrant, could I challenge this company from zero?"*

This skill helps analyze a company through its real business system. Instead of directly saying whether the company is good or bad, it asks how the company makes money, where a new entrant would get stuck, how competitors could attack it, and whether its advantages can turn into durable profit and cash flow.

**It analyzes from three perspectives**

- **Entrepreneur / competitor**: where a new entrant would get blocked.
- **Industry researcher**: the industry's scarce resources, control points, and profit pools.
- **Long-term investor**: whether the company has a durable moat worth tracking over time.

**Good for**

- Company research memos
- Industry entry-barrier analysis
- Moat pressure testing
- Competitor attack simulation
- Financial and business-model validation
- Long-term tracking metrics

**How to trigger**

```text
Use $company-moat-research to analyze NVIDIA's AI data center infrastructure business.

Use $company-moat-research to analyze Sandisk, focusing on NAND entry barriers, data center SSD opportunities, and long-term holding conditions.

Analyze Costco with the company moat research framework. Assume I am a new entrant trying to challenge it in five years.
```

→ [SKILL.md](./company-moat-research/SKILL.md) · [Research framework](./company-moat-research/references/research-framework.md)

### valuation-expectation-check

> *"Based on the previous analysis, how should we think about the current stock price?"*

This skill maps company research, industry research, earnings analysis, or moat analysis to the current stock price and valuation expectations. It does not answer whether to buy or sell. Instead, it breaks down what expectations are embedded in the current price, whether those expectations match the fundamentals, and which variables could drive a re-rating or de-rating.

**It focuses on**

- Growth, margin, and cash-flow expectations implied by current valuation.
- Whether those expectations match the underlying business analysis.
- What the market has likely priced in and what may still be underappreciated.
- What data could support further re-rating or trigger de-rating.
- The most important follow-up indicators.

**Good for**

- Follow-up stock price questions after company research
- Post-earnings valuation reassessment
- Valuation expectation checks for growth, cyclical, platform, and asset-heavy companies
- Market-implied expectation analysis
- Risk/reward framing

**How to trigger**

```text
Use $valuation-expectation-check to analyze what market expectations are implied by NVIDIA's current stock price.

Based on the previous Sandisk analysis, use $valuation-expectation-check to evaluate whether the current price already reflects NAND strength.

Is this company's current valuation expensive? Do not give buy/sell advice; break down market expectations and validation metrics.
```

→ [SKILL.md](./valuation-expectation-check/SKILL.md) · [Valuation framework](./valuation-expectation-check/references/valuation-framework.md)

### integrated-equity-research-report

> *"Turn the previous research into a Markdown report that can be archived."*

This skill merges moat research, valuation expectation checks, earnings analysis, or other investment research materials into a standardized Markdown research report with stable headings and clear evidence classification. It does not redo company analysis or valuation work; it deduplicates, compresses, standardizes, and preserves conclusions.

**It focuses on**

- Merging outputs from `company-moat-research` and `valuation-expectation-check`.
- Standardizing Markdown report headings, order, and metadata.
- Preserving confirmed facts, reasoned inferences, and assumptions to verify.
- Removing repeated sections while connecting moat conclusions with valuation expectations.
- Producing a formal research report suitable for archiving.

**Good for**

- Archiving multi-turn company research
- Organizing investment memos
- Standardizing outputs from different agents
- Combining moat analysis and valuation expectation checks
- Generating Markdown research reports

**How to trigger**

```text
Use $integrated-equity-research-report to turn the previous Tencent moat analysis and valuation expectation check into a Markdown research report.

Merge the previous $company-moat-research and $valuation-expectation-check outputs into a formal research report.

Generate a standardized company research report from these research materials. Do not give buy/sell advice.
```

→ [SKILL.md](./integrated-equity-research-report/SKILL.md) · [Report template](./integrated-equity-research-report/references/report-template.md)

### equity-research-pipeline

> *"/equity-research-pipeline Microsoft" — one command, complete research report.*

This skill chains moat research, valuation expectation checks, and report generation into a single end-to-end pipeline. Provide a company name and it runs all three steps in sequence, producing an archivable Markdown research report.

**It runs these steps in order**

1. **Moat research**: analyze business boundaries, industry barriers, moat sources, business model, and financial quality.
2. **Valuation check**: fetch the latest stock price, break down market-implied expectations, and compare them against the moat analysis.
3. **Report generation**: merge both analyses into a standardized Markdown research report.

**Good for**

- Quickly bootstrapping a company research archive
- Simplifying multi-step research workflows
- Batch-generating standardized research reports
- Situations where you don't want to trigger three separate skills manually

**How to trigger**

```text
Use $equity-research-pipeline to analyze Microsoft.

$equity-research-pipeline TSMC, save the report to ~/research/.

Run the end-to-end research pipeline for NVIDIA and produce a full report.
```

→ [SKILL.md](./equity-research-pipeline/SKILL.md)

### equity-comparison-advisor

> *"Across these research reports, which companies deserve priority research or allocation?"*

This skill reads multiple company research reports, extracts comparable fields, and produces table-first comparisons, rankings, risk-reward matrices, and conditional allocation frameworks. It is designed to run after `equity-research-pipeline` has generated reports for a group of companies.

**It focuses on**

- Summarizing business quality, growth certainty, valuation pressure, risk level, and expectation gaps across companies.
- Presenting conclusions through tables, ranking grids, and risk-reward matrices.
- Framing conditional suggestions such as priority research, staged allocation, waiting for valuation digestion, small-position observation, or watchlist only.
- Listing buy, wait, and reassessment conditions.
- Preserving data dates and evidence boundaries while avoiding unconditional buy/sell calls.

**Good for**

- Comparing the Magnificent Seven or other peer groups
- Summarizing multiple Markdown research reports
- Ranking portfolio candidates
- Building risk-reward matrices and investor-type matching
- Defining buy conditions, wait signals, and risk signals

**How to trigger**

```text
Use $equity-comparison-advisor to compare the Magnificent Seven reports under ~/research/magnificent-seven.

Based on these reports, compare which companies deserve priority research and which should wait for valuation digestion.

Use $equity-comparison-advisor to produce table-based rankings, a risk-reward matrix, and buy-condition tables.
```

→ [SKILL.md](./equity-comparison-advisor/SKILL.md) · [Comparison framework](./equity-comparison-advisor/references/comparison-framework.md)

---

## Repository Layout

```text
investment-research-skills/
├── README.md
├── README.en.md
├── LICENSE
├── company-moat-research/
│   ├── SKILL.md
│   ├── agents/
│   │   └── openai.yaml
│   └── references/
│       └── research-framework.md
├── valuation-expectation-check/
│   ├── SKILL.md
│   ├── agents/
│   │   └── openai.yaml
│   └── references/
│       └── valuation-framework.md
├── integrated-equity-research-report/
│   ├── SKILL.md
│   ├── agents/
│   │   └── openai.yaml
│   └── references/
│       └── report-template.md
├── equity-research-pipeline/
    ├── SKILL.md
    └── agents/
        └── openai.yaml
└── equity-comparison-advisor/
    ├── SKILL.md
    ├── agents/
    │   └── openai.yaml
    └── references/
        └── comparison-framework.md
```

---

## Contributing

Contributions are welcome. Suggested conventions:

- Keep each skill in its own directory.
- Every skill should include at least `SKILL.md`.
- Put detailed frameworks under `references/`.
- Do not commit `.DS_Store`, temporary files, private research materials, or unauthorized data.

---

[MIT License](./LICENSE) · Free to use, modify, and redistribute
