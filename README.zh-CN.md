# Researcher

一个面向 Claude Code 的前沿搜索与 ReAct 深度研究 skill。

这个 skill 的目标很明确：把研究行为从“搜一次、读摘要、直接总结”，改造成
“先建图、再跟线索、一直追到一手来源或证据图谱饱和”。

[English](README.md) | 中文

## 快速导航

- [这个 Skill 是干什么的](#这个-skill-是干什么的)
- [搜索策略](#搜索策略)
- [它和普通深搜有什么不同](#它和普通深搜有什么不同)
- [对科研问题为什么更友好](#对科研问题为什么更友好)
- [仓库结构](#仓库结构)
- [安装](#安装)
- [使用示例](#使用示例)
- [核心规则](#核心规则)
- [局限](#局限)

## 一眼看懂

| | 普通“深度搜索” | 这个 skill |
|---|---|---|
| 第一轮 | 搜索并总结 | 先广度建图 |
| 搜索结构 | 网页很多，结构较弱 | 明确维护证据图谱 |
| 线索选择 | 改写查询词 | 用 frontier 选分支 |
| 深度策略 | 常常广而浅 | 多分支 ReAct 深跳 |
| 时效规则 | 常常写死时间窗 | 按领域找最新可获得来源 |
| 停止规则 | 到轮数或上下文上限就停 | 研究图谱饱和才停 |
| 风格 | 聚合器 | 调查员 |

## 这个 Skill 是干什么的

很多所谓的“深度搜索”本质上还是广度聚合器：搜很多网页、抓很多内容、最后压缩成一段总结。
这当然有用，但它不像真正的研究员或调查员。

这个 skill 改的是搜索策略本身，核心有三步：

1. `先广度建图`
   第一轮不急着回答，而是先把领域地图铺开：综述、最新代表工作、基础文献、
   benchmark、争议和限制条件。
2. `然后维护多分支 frontier`
   不会过早只押一条线，而是保留多条活跃分支，动态决定下一轮追哪些。
3. `每条分支都按 ReAct 深跳`
   后续每轮都由上一轮结果驱动：
   `SEARCH / FETCH -> REASON -> NEXT JUMP`

所以它更像是在“沿着证据图谱调查”，而不是“堆网页后做摘要”。

## 搜索策略

这个 skill 的核心循环是：

```text
MAP -> BUILD FRONTIER -> DEEPEN -> REFLECT -> repeat
```

### 阶段 1：先建领域地图

第一轮明确是广度优先，任务不是回答问题，而是建立 field map。

它会尽量覆盖：
- 该领域当前能拿到的最新综述性来源
- 最近有代表性的工作
- 基础性、定义性的来源
- benchmark、dataset、标准或评测层
- criticism、limitation、replication、竞争路线

一个关键点是：它不会写死“最近一年”这种时间窗。

这里的“最新”指的是这个领域里“当前可获得的最新高质量来源”：
- 慢领域里，最新综述可能是几年前的
- 快领域里，可能就是最近几个月的
- 新方向里，可能根本没有正式综述，只能退到 tutorial、benchmark、perspective

### 阶段 2：构建 frontier，而不是只追一条线

建图后，这个 skill 会维护一个 frontier，也就是一组待追的候选线索，而不是马上锁死到一条路径。

典型的 branch 类型包括：
- 方法分支
- 证据分支
- benchmark 分支
- 作者 / 实验室分支
- 批评 / 限制分支
- 一手文档分支

这也是它和普通 citation chaining 最大的差异：它保留足够的分支宽度，避免 tunnel vision。

### 阶段 3：按 ReAct 深跳

对每条活跃分支，它都会执行：

```text
SEARCH / FETCH -> REASON -> NEXT JUMP
```

并且每一轮都记录：
- `[Finding]` 这一步确认或推翻了什么
- `[Lead]` 出现了什么新线索
- `[Gap]` 哪个关键 claim 还没有一手来源
- `[Next Jump]` 下一跳为什么值得追

这意味着后续的搜索不是简单改写关键词，而是根据新发现的结构做跳转。

### 阶段 4：按饱和停止，而不是按轮数停止

这个 skill 不会因为“已经搜了 3 轮”就停。

它的停止标准是研究图谱接近饱和：
- 主要分支已经覆盖
- 关键 claim 已经挂到一手来源或最高价值来源
- 新搜索结果大多只是返回已知节点
- 剩余分支的信息增量明显变低

## 它和普通深搜有什么不同

这个 skill 主要是为了避开三类常见失败模式：

1. `广而浅`
   搜很多，但没有真正追到关键线索。
2. `过早变窄`
   太早押一条主线，漏掉其他重要分支。
3. `伪时效性规则`
   把“最近”粗暴写成“最近一年”，导致在慢领域直接失真。

它的设计组合是：
- breadth-first 建图
- 多分支 frontier 管理
- ReAct 驱动深跳
- 按领域切换 source hierarchy
- 按饱和而不是按轮数停止

## 对科研问题为什么更友好

这个 skill 对科研 / 技术研究做了专门优化，目标是保证它在文献综述类任务里也好用。

它会同时保住领域的两端：
- 最新前沿
- 基础源头

优先覆盖：
- 最新可获得的 review / survey / tutorial / benchmark / perspective
- 最近的代表性论文
- foundational paper
- benchmark 和评测协议
- criticism / limitation / replication

它还允许“一手来源”的定义按领域变化：
- 科研：原始论文、附录、代码、数据集、benchmark 文档
- 产业：财报、监管文件、专利、标准、官方技术文档
- 医学：systematic review、RCT、指南、registry、监管来源

## 仓库结构

```text
researcher-skill/
├── README.md
├── README.zh-CN.md
└── researcher/
    ├── SKILL.md
    └── references/
        └── research-heuristics.md
```

- `researcher/SKILL.md`
  放核心流程和硬约束。
- `researcher/references/research-heuristics.md`
  放 frontier 打分、source hierarchy、query shaping、剪枝和饱和规则。

这样拆是故意的：主 prompt 保持简洁，复杂规则按需加载。

## 一个简化示例

```text
Round 1: Map "LLM hallucination mitigation"
  -> review / benchmark / recent papers / foundational papers / criticism
  -> 得到几条分支：
     A. retrieval-based methods
     B. decoding-time methods
     C. internal steering methods
     D. benchmark validity / limitations

Round 2: Deepen A + C + D
  -> A 追到 benchmark 和 dataset 细节
  -> C 追到最新的表示操控类论文
  -> D 追到 replication 和 evaluation limitation

Round 3+: Jump to primary sources
  -> 向后跳、向前跳、横向跳、向下跳
  -> 读原始论文、附录、代码、benchmark 文档
  -> 弱分支降权，高价值分支继续保留

Stop:
  -> 不再出现新的方法类、新证据层级或新争议
```

## 安装

克隆仓库：

```bash
git clone https://github.com/recomby-ai/researcher-skill.git
```

安装到 Claude Code：

```bash
cp -r researcher-skill/researcher ~/.claude/skills/
```

然后这样使用：

```text
/researcher 你的问题
```

## 使用示例

```text
/researcher What are the current solutions to LLM hallucination?
/researcher CRISPR off-target detection methods — state of the art
/researcher Is solid-state battery mass production realistic by 2026?
/researcher Verify whether this industry claim traces back to a primary source
```

## 核心规则

- 不能搜一轮就回答。
- 重要 claim 不能只靠综述或二手总结。
- 除非用户明确要求，否则不要把时间窗写死。
- 不要过早只剩一个 branch。
- 除非 field map 确实有盲点，否则不要重新退化成泛泛广搜。
- 必须主动找反证，不只找支持证据。
- 按饱和停止，不按轮数停止。

## 局限

- 无法通过普通 WebSearch 直接访问 Google Scholar。
- 不一定能读到付费论文全文。
- 仍然受限于搜索工具和抓取工具能接触到的公开网页。
- 它不是严格意义上的 systematic review 引擎。

## License

MIT
