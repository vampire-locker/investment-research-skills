# 投资研究 路由矩阵

本文件定义用户意图到子技能的映射规则。总入口 SKILL.md 在执行前必须完成路由，再进入子技能。

---

## 路由协议

1. 先执行路由，再进入子技能。不要跳过路由直接开始分析。
2. 匹配目标类型 × 用户意图，选最优入口。
3. 跨模块路径：匹配后按标准工作流依次执行多个子技能。
4. 路由失败时：若用户意图无法匹配任何现有子技能，向用户说明，并建议最接近的可用分析。
5. 多意图同时命中时：选择覆盖范围最大的入口（一站式 > 单项分析 > 局部问答）。例如用户同时提到"护城河"和"估值"，应路由到 `equity-research-pipeline`（覆盖两者）。如有歧义，向用户确认：「你是想完整研究这家公司，还是只看 [A] 或 [B] 其中一个方面？」

---

## 维度一：分析对象

| 对象 | 推荐入口 | 说明 |
| --- | --- | --- |
| 单一公司 | `equity-research-pipeline` | 一站式，覆盖护城河 + 估值 + 报告 |
| 行业/赛道 | `sector-research` | 产业链 + 竞争格局 + 周期位置 |
| 多家公司（已有报告） | `equity-comparison-advisor` | 横向比较 + 排序 + 配置建议 |
| 多家公司（无报告） | 先 `equity-research-pipeline` 逐个生成，再 `equity-comparison-advisor` | 分两步 |

## 维度二：用户意图 → 子技能映射

### 行业与赛道

| 用户说 | 路由到 |
| --- | --- |
| "分析行业" "赛道研究" "产业链" "竞争格局" "行业景气" "周期位置" | `sector-research` |
| "这个赛道值不值得看" "哪个环节利润最厚" "产业链利润往哪里走" | `sector-research` |
| "技术路线对比" "政策环境" "供需格局" "市场结构" | `sector-research` |

### 公司深度研究

| 用户说 | 路由到 |
| --- | --- |
| "护城河" "进入壁垒" "竞争优势" "竞争攻击" "从 0 做能不能挑战" | `company-moat-research` |
| "商业模式" "利润来源" "关键资源" "护城河可持续性" | `company-moat-research` |
| "长期跟踪" "长期持有条件" | `company-moat-research` |

### 估值与股价

| 用户说 | 路由到 |
| --- | --- |
| "股价怎么看" "估值贵不贵" "当前价格隐含什么" "市场预期" | `valuation-expectation-check` |
| "重估" "杀估值" "估值风险" "上行验证" "下行风险" | `valuation-expectation-check` |
| "当前价格是否透支" "市场在赌什么" | `valuation-expectation-check` |

### 报告整合

| 用户说 | 路由到 |
| --- | --- |
| "整理报告" "生成研报" "合并输出" "沉淀" "归档" "统一格式" | `integrated-equity-research-report` |

### 一站式研究

| 用户说 | 路由到 |
| --- | --- |
| "分析公司" "研究公司" "帮我看看XX" "完整分析XX" "出份报告" | `equity-research-pipeline` |
| 用户只提供公司名，未说明要分析什么 | `equity-research-pipeline` |

### 横向比较

| 用户说 | 路由到 |
| --- | --- |
| "对比这几家" "比较" "排序" "谁更值得" "买入优先级" | `equity-comparison-advisor` |
| "七姐妹" "配置建议" "风险收益排序" "组合候选" | `equity-comparison-advisor` |

## 维度三：输出期望

| 用户期望 | 处理 |
| --- | --- |
| 默认（未指定） | 按子技能默认输出模式 |
| "简短" "快速" "结论就好" | 加载子技能的简版模式（如有） |
| "保存" "写文件" "生成 md" | 加载子技能的归档模式，输出到文件 |
| "只回答某个问题" | 局部问答模式，不生成完整报告 |

---

## 标准工作流路径

### 路径 1：从赛道到公司

```
sector-research（确定关键环节）
  → equity-research-pipeline（逐个研究候选公司）
    → equity-comparison-advisor（横向比较排序）
```

### 路径 2：单公司完整研究

```
equity-research-pipeline（内部依次调用）
  → company-moat-research（护城河）
  → valuation-expectation-check（估值验证）
  → integrated-equity-research-report（报告整合）
```

### 路径 3：已有研究 → 估值追问

```
company-moat-research（或 equity-research-pipeline）输出
  → valuation-expectation-check（基于基本面追问股价）
```

### 路径 4：多公司批量比较

```
equity-research-pipeline × N（批量生成单公司报告）
  → equity-comparison-advisor（横向比较排序）
```
