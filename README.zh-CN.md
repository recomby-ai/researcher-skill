# Researcher

一个单独可安装的 research skill，给 Claude Code / Codex 用。

一个自包含 skill 文件，围绕一条清晰研究主轴展开。

```text
纵轴历史 + 横轴对比 -> 横纵交汇判断
```

[English](README.md) | 中文

## 这个 Skill 是干什么的

`researcher` 适合这类研究任务：

- 问题开放
- 需要多来源交叉验证
- 最终需要判断，不只是摘录
- 很容易被 hype、浅总结、单边叙事带偏

它可以处理的典型任务包括：

- 摸清一个新行业或领域
- 调查一家公司或产品
- 验证一个说法或叙事
- 比较选项、做决策支持
- 找真实机会，而不是只看热闹
- 看从业者真实体验和隐藏摩擦
- 做学术文献综述和技术调研

## 架构

一个合并后的 research skill：

```text
researcher/
└── skills.md                         ← 横纵分析研究方法
```

**skills.md** 包含完整方法：前置准备、信息收集、纵轴分析、横轴分析、横纵交汇洞察、
对象类型适配、证据和引用规则、输出结构、写作标准和最终质检清单。

`skills.md` 本体使用中文，方便直接阅读和修改；YAML metadata 里保留英文触发词，
让英文研究请求也能触发。

## 设计核心

### 1. 一个核心方法

这个 skill 不是研究技巧堆叠。每次研究都按一条主线走：

- 纵轴：它是怎么一步步变成今天这样的。
- 横轴：它现在在同类、替代品、用户和利益关系里处在什么位置。
- 交汇判断：纵轴和横轴合在一起揭示了什么。

### 2. 证据服务于两条轴

证据不是为了堆来源，而是为了支撑纵轴和横轴。skill 仍然区分 official、
behavioral、operator、lived experience、adversarial、market proxy、artifact 等来源。

### 3. 判断前必须反证

每个强 thesis 都要先被攻击：批评、失败案例、方法问题、对抗来源、利益动机和行为证据都要看。

### 4. 自适应输出

Skill 默认给出简洁的 chat answer。只有在用户明确要求、提供输出路径，或任务太大不适合
内联呈现时，才创建持久化研究文档。

## 安装

克隆：

```bash
git clone https://github.com/recomby-ai/researcher-skill.git
```

安装到 Claude Code：

```bash
mkdir -p ~/.claude/skills/researcher
cp researcher-skill/researcher/skills.md ~/.claude/skills/researcher/SKILL.md
```

安装到 Codex：

```bash
mkdir -p ~/.codex/skills/researcher
cp researcher-skill/researcher/skills.md ~/.codex/skills/researcher/SKILL.md
```

## 网页版上传

如果运行环境要求入口文件名必须是 `SKILL.md`，上传前把 `researcher/skills.md`
重命名为 `SKILL.md`。除此之外它是自包含文件。

## 使用示例

```text
Use $researcher to map the AI agent engineering job market.
Use $researcher to verify whether this industry claim is actually true.
Use $researcher to do a horizontal-vertical analysis of this product.
Use $researcher to compare quant, AI infrastructure, and applied ML for a math undergraduate.
Use $researcher to find the strongest opportunities in vertical AI.
Use $researcher to stress-test this startup before I take the offer.
Use $researcher to find what practitioners really complain about in production agent systems.
Use $researcher to review the literature on retrieval-augmented generation.
Use $researcher to do due diligence on this company's Series B narrative.
```

## 局限

- 仍然受限于公开网页和当前搜索/抓取工具
- 某些来源会被登录或付费墙挡住
- 社区和社交来源是高价值信号，但不等于自动为真
- 它是研究方法增强，不是领域知识的替代品

## License

MIT
