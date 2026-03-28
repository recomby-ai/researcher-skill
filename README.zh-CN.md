# Researcher

一个单独可安装的 research skill，给 Claude Code / Codex 用。

一个核心引擎，三个领域包，按研究目的组装。

```text
FRAME → MAP → FRONTIER → DEEPEN → CHALLENGE → SYNTHESIZE
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

一个核心引擎 + 三个按需加载的领域包：

```text
researcher/
├── SKILL.md                          ← 核心研究引擎
└── references/
    ├── business.md                   ← 行业 + 公司 + 职业
    ├── academic.md                   ← 论文 + benchmark + 技术谱系
    └── claim-verification.md         ← 跨领域事实核查
```

**SKILL.md** 包含完整研究方法论：六阶段循环、证据分类体系、frontier 管理、饱和度规则、
反证纪律、工具使用、预算控制、输出模板。

**领域包** 包含特定领域的战术：去哪搜、用什么 query、提取什么信号、领域特有的
challenge paths、以及该类研究的输出模板。

Agent 每次都加载 SKILL.md，然后根据研究类型加载 1-2 个领域包。

## 设计核心

### 1. 先看证据类型，不是先堆网页

这个 skill 把互联网看成一个混合证据环境：

- official — 机构怎么说
- behavioral — 实际怎么做
- operator — 有经验的人怎么说
- lived experience — 从业者在论坛、社交上怎么报告
- adversarial — 做空报告、批评者、诉讼、投诉
- market proxy — 招聘、定价、融资、采用率信号
- artifact — 论文、代码、文档、数据集、法律文件

### 2. 先广度建图，再受控深挖

第一轮不是"搜到够总结就停"。而是：

- 有控制的 breadth-first map（4-6 次搜索）
- 然后建立 2-4 条 active frontier
- 再按线索驱动继续深挖

### 3. 强制反证路径

每个强 thesis 必须先跑 challenge path 才能合成结论。skill 要求检查对立动机、
对抗性来源、和行为证据之后才能下结论。

### 4. 强制外显推理

Skill 会写 `research-{topic}.md` 并在过程中持续更新，让研究路径可见可审计。

## 安装

克隆：

```bash
git clone https://github.com/recomby-ai/researcher-skill.git
```

安装到 Claude Code：

```bash
cp -R researcher-skill/researcher ~/.claude/skills/
```

安装到 Codex：

```bash
cp -R researcher-skill/researcher ~/.codex/skills/
```

## 网页版上传

打包 `researcher/` 目录上传即可，自包含结构。

## 使用示例

```text
Use $researcher to map the AI agent engineering job market.
Use $researcher to verify whether this industry claim is actually true.
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
