**中文** · [English](./README.en.md)

# Investment Research Skills

#### 投资研究用的 Agent Skills 集合

[![License](https://img.shields.io/badge/License-MIT-3B82F6?style=for-the-badge)](./LICENSE)
[![Skills](https://img.shields.io/badge/Skills-1-10B981?style=for-the-badge)](#-skills)
[![AgentSkills](https://img.shields.io/badge/AgentSkills-Standard-8B5CF6?style=for-the-badge)](https://agentskills.io)

![Claude Code](https://img.shields.io/badge/Claude_Code-Skill-D97706?style=flat-square&logo=anthropic&logoColor=white)
![Codex](https://img.shields.io/badge/Codex-Skill-10B981?style=flat-square&logo=openai&logoColor=white)
![OpenCode](https://img.shields.io/badge/OpenCode-Skill-3B82F6?style=flat-square)

这里收集的是投资研究场景下可复用的 Agent Skills。每个 skill 都是一个独立的结构化指令集，遵循 [Agent Skills](https://agentskills.io) 开放格式，可被支持 `SKILL.md` 的 Agent 客户端加载。

当前仓库以中文研究输出为主，适合公司研究、行业壁垒分析、护城河判断、竞争对手攻击模拟、财务与商业模式验证等场景。

---

## 目录

| 名字 | 一句话 | 入口 |
| --- | --- | --- |
| [**company-moat-research（公司护城河研究）**](#-company-moat-research公司护城河研究) | 从新进入者、产业研究员、长期投资者三个视角拆解公司护城河和行业进入壁垒 | [SKILL.md](./company-moat-research/SKILL.md) |

---

## 安装

在支持 Skills 的 Agent 里，可以直接让 Agent 安装指定目录：

```text
帮我安装这个 skill：https://github.com/vampire-locker/investment-research-skills/tree/main/company-moat-research
```

也可以手动安装到 Codex：

```bash
git clone git@github.com:vampire-locker/investment-research-skills.git
mkdir -p ~/.codex/skills
cp -R investment-research-skills/company-moat-research ~/.codex/skills/
```

Claude Code、OpenCode 等其他客户端请按各自的 skill 导入方式安装 `company-moat-research` 目录。

---

## ✨ Skills

### company-moat-research（公司护城河研究）

> *“如果我是一个资金充足、执行力很强的新进入者，能不能从 0 开始挑战这家公司？”*

这个 skill 用来研究一家公司所在的行业或细分业务。它不会直接判断“好不好”，而是先把公司放回真实业务系统里，拆解它靠什么赚钱、行业从 0 做起来会卡在哪里、竞争对手怎么进攻，以及这些优势能不能转化为长期利润和现金流。

**它会从三个视角分析**

- **创业者 / 竞争对手**：如果从 0 做同样的生意，最难突破哪些环节。
- **产业研究员**：行业真正的关键资源、稀缺能力和利润来源是什么。
- **长期投资者**：公司是否具备可持续护城河，是否值得长期跟踪或长期持有。

**适合**

- 公司研究和投资备忘录
- 行业进入壁垒分析
- 护城河压力测试
- 竞争对手攻击模拟
- 财务和商业模式验证
- 长期跟踪指标梳理

**怎么触发**

```text
使用 $company-moat-research 分析英伟达所在的 AI 数据中心基础设施业务。

$company-moat-research 分析闪迪，重点看 NAND 行业进入壁垒、数据中心 SSD 机会和长期持有条件。

用公司护城河研究框架分析 Costco，假设我是新进入者，未来 5 年想挑战它。
```

→ [SKILL.md](./company-moat-research/SKILL.md) · [研究框架](./company-moat-research/references/research-framework.md)

---

## 仓库结构

```text
investment-research-skills/
├── README.md
├── README.en.md
├── LICENSE
└── company-moat-research/
    ├── SKILL.md
    ├── agents/
    │   └── openai.yaml
    └── references/
        └── research-framework.md
```

---

## 贡献

欢迎提交新的投资研究类 skill，或改进现有研究框架。建议保持：

- 每个 skill 一个独立目录。
- 每个 skill 至少包含 `SKILL.md`。
- 详细框架放在 `references/` 下。
- 不提交 `.DS_Store`、临时文件、私有资料或未授权数据。

---

[MIT License](./LICENSE) · 自由使用 / 修改 / 再分发
