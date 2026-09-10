# OSINT Evidence Forge（简体中文）

[English](README.md) | [繁體中文](README.zh-TW.md) | [Русский](README.ru.md) | [Українська](README.uk.md)

**面向 AI 智能体的开源情报认知卫生技能。**

OSINT Evidence Forge 是一个 [Hermes Agent](https://hermes-agent.nousresearch.com) 技能，也可作为通用 agent skill 使用。它教会 AI 智能体从异质证据中重建调查线索：聊天记录、图片、视频、元数据、时间线、财务信息、交通模式与地理线索。

它的核心价值**不是**猜地点的技巧，而是一条在证据嘈杂、残缺、自相矛盾且被后验污染时，让智能体保持诚实的纪律流水线：

```text
字面证据 → 来源鉴定 → 竞争假设
→ 区分度加权 → 反事实检验
→ 修正传播 → 有界结论
```

## 它强制执行什么

本技能围绕十条**硬性不变量**构建，包括：

1. **T0/T1/H 时间边界** —— 区分"当时已知""后来获得""仅事后可知"；后见之明永不追溯性地正当化此前的决策。
2. **推断前逐字解析** —— 限定词、介词、代词、约略语在改写前先解析；解析一旦改变，所有依赖结论全部作废。
3. **竞争假设账本** —— 结论是可修订的候选，标注支持、矛盾、前提假设与失效条件；新证据必须对*每一个*候选检验，绝不硬套当前最优。
4. **兼容 ≠ 支持** —— "无冲突"计零分，永不提升候选。
5. **三轴证据评分** —— 可靠性 × 区分度 × 独立性；真实但无区分度的事实无法定位任何东西。
6. **漏斗而非链条** —— 结构性约束（交通、目的地、时距、人际关系）先于视觉匹配求交；结论必须通过消融测试。
7. **约束带而非点** —— 物理测量与口头时间估计以约束带传播，拒绝假精确。
8. **地理定位的预测性验证** —— 宣布位置前，先预测该机位还应看到什么，并逐项确认。
9. **负面证据需要覆盖记录** —— "我找了没找到"只有在记录搜索覆盖范围与可检测性之后才算证据。
10. **安全边界** —— 禁止骚扰、开盒、无正当理由的私人精确位置；生物识别保留为外部授权人类步骤；福利紧急情况转交真实救援方。

## 安装

### skills.sh（支持 Claude Code 及 40+ 种智能体）

```bash
npx skills add infinmalum/osint-evidence-forge
```

### Hermes Agent

```bash
hermes skills tap add infinmalum/osint-evidence-forge
hermes skills install infinmalum/osint-evidence-forge
```

或直接从 SKILL.md URL 安装：

```bash
hermes skills install https://raw.githubusercontent.com/infinmalum/osint-evidence-forge/main/SKILL.md
```

### 其他智能体（Cursor 及兼容 SKILL.md 的运行时）

本技能采用标准 `SKILL.md` + `references/` 布局，无需执行代码。将本仓库指向你的运行时技能目录，或把 `SKILL.md` 和 `references/` 复制进其技能文件夹即可。

## 方法论来源

流程提炼自真实调查及其事后复盘，包括 Bellingcat 公开方法风格的地理定位与核验案例研究（渐进式定位、时间定位、阴影约束、搜索网格、来源恢复），以及一次平民福利寻人重建。不包含任何真实案件名称、当事人、地点或数据——所有示例均为虚构。

## 安全性

本技能面向记者、研究人员、保护专业人员与合法调查者。它明确拒绝骚扰、跟踪、开盒和对私人个体未经正当理由的曝光。完整的"权限 + 手段"模型见 `SKILL.md` 中的 *Safety and Authorization Boundary* 章节。

## 许可证

[MIT](LICENSE)
