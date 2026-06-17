[中文](./README.md) · **English**

# Investment Research Skills

#### Agent Skills for investment research workflows

[![License](https://img.shields.io/badge/License-MIT-3B82F6?style=for-the-badge)](./LICENSE)
[![Skills](https://img.shields.io/badge/Skills-2-10B981?style=for-the-badge)](#-skills)
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
```

For Claude Code, OpenCode, and other clients, import the desired skill directory according to the client's current skill workflow.

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

---

## Repository Layout

```text
investment-research-skills/
├── README.md
├── README.en.md
├── LICENSE
├── company-moat-research/
    ├── SKILL.md
    ├── agents/
    │   └── openai.yaml
    └── references/
        └── research-framework.md
└── valuation-expectation-check/
    ├── SKILL.md
    ├── agents/
    │   └── openai.yaml
    └── references/
        └── valuation-framework.md
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
