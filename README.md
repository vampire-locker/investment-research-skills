# Investment Research Skills

[中文](README.md) | [English](README.en.md)

面向支持 Agent Skills 格式的 AI 代理的投资研究类 Skills 集合，例如 Codex、Claude Code 以及其他兼容 `SKILL.md` 规范的客户端。

这个仓库不是单一 skill 项目，而是投资研究工作流集合。当前已包含公司护城河研究，后续可以继续加入行业链研究、财报质量检查、管理层电话会分析、竞争格局跟踪、估值假设拆解等投资相关 skills。

仓库以中文为主，英文文档用于说明兼容性和方便国际用户理解。

## 兼容性

本仓库采用 Agent Skills 的通用目录结构：每个 skill 是一个独立目录，至少包含 `SKILL.md`，并可按需包含 `references/`、`scripts/`、`assets/` 等资源目录。

- Codex：可将单个 skill 目录复制到 `~/.codex/skills/` 使用。
- Claude Code / Claude Skills：可按 Claude 客户端当前的导入方式，把单个 skill 目录作为 Agent Skill 使用。
- 其他兼容客户端：只要支持 `SKILL.md` + 资源目录的 Agent Skills 格式，通常可以复用本仓库中的 skill。

不同客户端的安装路径和导入方式可能不同，请以对应客户端的最新文档为准。本仓库中的 `company-moat-research` 不包含可执行脚本，主要是结构化研究指令和参考框架，因此跨客户端迁移成本较低。

## Skills

| Skill | 说明 | 适用场景 |
| --- | --- | --- |
| `company-moat-research` | 公司与行业护城河研究 | 分析公司所在细分业务、从 0 进入行业的难点、竞争攻击路径、关键资源和利润来源、商业模式质量、长期跟踪条件 |

## 快速安装

如果已经配置 GitHub SSH，可以先克隆仓库：

```bash
git clone git@github.com:vampire-locker/investment-research-skills.git
cd investment-research-skills
```

安装到 Codex：

```bash
mkdir -p ~/.codex/skills
cp -R company-moat-research ~/.codex/skills/
```

安装后，可以这样调用：

```text
使用 $company-moat-research 分析英伟达所在的 AI 数据中心基础设施业务。
```

或：

```text
$company-moat-research 分析闪迪，重点看 NAND 行业进入壁垒、数据中心 SSD 机会和长期持有条件。
```

## 使用方式

推荐提问格式：

```text
使用 $company-moat-research 分析【公司名】所在的【行业/细分业务】。

请假设我是一个资金充足、执行力很强的新进入者，准备从 0 开始做同样的生意，并在 3-10 年内挑战它。

请重点分析：
1. 公司到底靠哪些业务赚钱
2. 行业从 0 做起来的完整流程
3. 最难突破的 5-7 个环节
4. 目标公司在关键环节里的位置
5. 竞争对手的低/中/高预算攻击路径
6. 护城河能否转化为利润、现金流或 ROIC
7. 未来 3 年最重要的验证指标

请区分已确认事实、基于事实的合理推断、需要进一步验证的假设。
不要给买入/卖出建议，只判断是否值得长期跟踪或长期持有。
```

## 目录结构

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

## 设计原则

- 中文优先：skill 正文和研究框架使用中文，减少标题和输出格式混乱。
- 事实优先：明确区分已确认事实、合理推断和需要验证的假设。
- 不给买卖建议：输出长期跟踪条件、验证指标和投资逻辑变化信号。
- 不机械套模板：完整框架用于保证覆盖面，但回答应围绕目标公司的真实业务和行业瓶颈展开。
- 集合仓库：README 描述整个投资研究 skills 集合，具体 skill 的细节放在各自目录中。

## 卸载

删除已安装的 skill：

```bash
rm -rf ~/.codex/skills/company-moat-research
```

## 贡献

欢迎提交新的投资研究类 skill，或改进现有研究框架。建议保持以下约定：

- 每个 skill 独立成目录。
- 每个 skill 必须包含 `SKILL.md`。
- 详细框架放在 `references/` 下，避免 `SKILL.md` 过长。
- 对外文档优先中文，同时补充英文 README。
- 不提交 `.DS_Store`、临时文件、私有资料或未授权数据。

## 许可

本项目使用 MIT License。详见 [LICENSE](LICENSE)。
