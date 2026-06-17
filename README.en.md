# Investment Research Skills

[中文](README.md) | [English](README.en.md)

A collection of investment research skills for AI agents that support the Agent Skills format, including Codex, Claude Code, and other clients compatible with `SKILL.md`.

This is not a single-skill project. It is intended to grow into a broader investment research workflow collection. The repository currently includes company moat research, and future skills may cover industry-chain mapping, financial statement quality checks, earnings-call analysis, competitive landscape tracking, and valuation-assumption review.

The repository is Chinese-first. English documentation is provided for compatibility notes and discoverability.

## Compatibility

This repository follows the Agent Skills directory structure: each skill is a standalone directory containing at least `SKILL.md`, and may include resource directories such as `references/`, `scripts/`, and `assets/`.

- Codex: copy a skill directory into `~/.codex/skills/`.
- Claude Code / Claude Skills: import or register a skill directory according to the current Claude client workflow.
- Other compatible clients: if the client supports the `SKILL.md` + resource-directory Agent Skills format, these skills should be reusable.

Client-specific install paths and import flows may change, so follow the latest documentation for each client. The current `company-moat-research` skill contains no executable scripts; it is mainly structured research instructions and reference material, which makes it relatively portable across clients.

## Skills

| Skill | Description | Use Cases |
| --- | --- | --- |
| `company-moat-research` | Company and industry moat research | Analyze a company's business boundary, industry entry barriers, competitor attack paths, scarce resources, profit pools, business model quality, and long-term tracking conditions |

## Quick Install

If you have GitHub SSH configured, clone the repository first:

```bash
git clone git@github.com:vampire-locker/investment-research-skills.git
cd investment-research-skills
```

Install the skill for Codex:

```bash
mkdir -p ~/.codex/skills
cp -R company-moat-research ~/.codex/skills/
```

Then invoke it:

```text
Use $company-moat-research to analyze NVIDIA's AI data center infrastructure business.
```

Or:

```text
Use $company-moat-research to analyze Sandisk, focusing on NAND entry barriers, data center SSD opportunities, and long-term tracking conditions.
```

## Recommended Prompt

```text
Use $company-moat-research to analyze [company] in [industry/sub-segment].

Assume I am a well-funded and highly capable new entrant trying to build the same business from zero and challenge the company within 3-10 years.

Focus on:
1. How the company actually makes money
2. The complete process of building the industry from zero
3. The 5-7 hardest bottlenecks
4. The company's position in those bottlenecks
5. Low/mid/high budget competitor attack paths
6. Whether the moat can convert into profit, cash flow, or ROIC
7. The five most important validation metrics for the next three years

Separate confirmed facts, reasonable inferences, and assumptions that need verification.
Do not give buy/sell advice; judge whether the company deserves long-term tracking or long-term holding consideration.
```

## Repository Layout

```text
investment-research-skills/
├── README.md
├── README.en.md
├── LICENSE
├── .gitignore
└── company-moat-research/
    ├── SKILL.md
    ├── agents/
    │   └── openai.yaml
    └── references/
        └── research-framework.md
```

## Design Principles

- Chinese-first: the skill body and framework are written in Chinese to keep output headings and structure consistent.
- Evidence-first: clearly separate confirmed facts, reasonable inferences, and assumptions that need verification.
- No buy/sell advice: focus on long-term tracking conditions, validation metrics, and thesis-change signals.
- Avoid mechanical templates: use the full framework for coverage, but tailor the answer to the target company's real business and industry bottlenecks.
- Collection repository: the README describes the broader investment research skills collection; each skill keeps its own detailed instructions in its directory.

## Uninstall

Remove the installed skill:

```bash
rm -rf ~/.codex/skills/company-moat-research
```

## Contributing

Contributions are welcome. Suggested conventions:

- Keep each skill in its own directory.
- Every skill must include `SKILL.md`.
- Put detailed frameworks under `references/` to keep `SKILL.md` concise.
- Keep public documentation Chinese-first, with English documentation when useful.
- Do not commit `.DS_Store`, temporary files, private research materials, or unauthorized data.

## License

MIT License. See [LICENSE](LICENSE).
