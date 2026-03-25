# product-optimize

A Claude Code skill for systematic product optimization — discover issues, document checklist, analyze dependencies, then iteratively discuss, implement, review, and commit.

Claude Code 自定义 Skill，用于系统性产品优化：发现问题 → 记录清单 → 依赖分析 → 逐项（讨论 → 实施 → 验收 → 提交）。

## Why This Skill? / 为什么需要这个 Skill？

AI coding tools are great at building demos from scratch, but turning a demo into a production-quality product means hours of polishing details — and that's where most people get stuck. This skill is designed to solve three real pain points:

AI 编程工具擅长从零搭建 demo，但把 demo 打磨成生产级产品需要大量时间投入在细节上 — 这正是大多数人卡住的地方。这个 Skill 解决三个真实痛点：

### 1. From Demo to Production / 从 Demo 到生产级

The typical AI coding loop is: you spot a problem → tell AI → AI fixes it → you spot another → repeat. **You are the driver, AI is the executor.** But detail work is divergent — you don't know what problems exist until you stumble upon them.

典型的 AI 编程循环是：你发现问题 → 告诉 AI → AI 修复 → 你再发现 → 重复。**你是推动者，AI 是执行者。** 但打磨细节的工作是发散的 — 你不知道还有多少问题，只能靠自己一个个撞上。

This skill **reverses the dynamic**: AI proactively discovers issues across visual, logical, and code-quality dimensions, proposes solutions, and drives the workflow. You only make key decisions — approve, reject, or redirect. What used to take hours of manual back-and-forth becomes a streamlined, AI-driven process.

这个 Skill **反转了这个关系**：AI 主动从视觉、逻辑、代码质量等维度发现问题，提出方案，推动流程。你只需要做关键决策 — 同意、否决或调整方向。原本需要数小时反复沟通的工作，变成了 AI 驱动的流水线。

### 2. Articulate the Inarticulate / 把"说不出的不舒服"变成解决方案

Sometimes you look at a page and feel something is off — but you can't explain what or why. You just know it's not right.

有时候你看着一个页面，总觉得哪里不对 — 但说不出具体是什么、为什么。就是感觉不舒服。

This skill systematically scans across visual hierarchy, information architecture, data accuracy, code consistency, and competitive benchmarks. It **translates your vague intuition into a concrete, prioritized list of specific problems** — each with a clear explanation of what's wrong and a deliverable fix. In real-world use, a single run typically uncovers 10+ optimization points that the user hadn't consciously identified.

这个 Skill 系统性地扫描视觉层级、信息架构、数据准确性、代码一致性和竞品对比。它能**把你模糊的直觉翻译成具体的、有优先级的问题清单** — 每个问题都有清晰的解释和可交付的修复方案。实际使用中，一次运行通常能发现 10+ 个用户自己没有意识到的优化点。

### 3. Traceable Improvement / 可追溯的改进过程

Traditional "optimize this" requests result in one big commit with mixed changes. Days later, nobody remembers what was changed or why.

传统的"优化一下"产出的是一个混杂的大 commit。几天后，没人记得改了什么、为什么改。

This skill enforces **one commit per optimization item**, paired with a checklist document that records the original problem, the goal, and the outcome for each item. The result is not just better code — it's a **complete decision log** that's valuable for team collaboration, code review, and future maintenance.

这个 Skill 强制**每个优化项对应一个独立 commit**，配合清单文档记录每项的现状、目标和结论。产出的不只是更好的代码，还有一份**完整的决策记录**，对团队协作、代码评审和后续维护都有价值。

## Installation / 安装

```bash
mkdir -p ~/.claude/skills/product-optimize
cp SKILL.md ~/.claude/skills/product-optimize/SKILL.md
```

Or clone and copy / 或克隆后复制:

```bash
git clone https://github.com/bitdezi/claude-skill-product-optimize.git
mkdir -p ~/.claude/skills/product-optimize
cp claude-skill-product-optimize/SKILL.md ~/.claude/skills/product-optimize/
```

## Usage / 使用

In Claude Code, invoke the skill with / 在 Claude Code 中调用:

```
/product-optimize <target description>
```

Examples / 示例:

```
/product-optimize token detail page trade panel
/product-optimize user settings page
/product-optimize checkout flow
```

## How It Works / 工作流程

The skill guides Claude through a structured 5-phase optimization workflow:

该 Skill 引导 Claude 执行结构化的 5 阶段优化流程：

### Phase 1: Discovery / 发现问题

Examine the target code with fresh eyes across 4 dimensions:

以全新视角审视目标代码，从 4 个维度识别优化点：

- **Visual & UX / 视觉与体验**: hierarchy, information architecture, consistency, responsiveness / 视觉层级、信息架构、组件一致性、响应式
- **Data & Logic / 数据与逻辑**: accuracy, edge cases, consistency / 数据准确性、边界情况、一致性
- **Code Quality / 代码质量**: anti-patterns, hardcoded values, reuse opportunities / 反模式、硬编码值、复用机会
- **Competitive Reference / 竞品参考**: how similar products solve the same problem / 同类产品的设计逻辑

### Phase 2: Checklist / 记录清单

Create a structured optimization checklist document with status tracking.

创建结构化的优化清单文档，包含现状、目标、状态追踪。

### Phase 3: Dependency Analysis / 依赖分析

Analyze relationships between items to determine optimal execution order:

分析优化项之间的依赖关系，确定最优执行顺序：

- **Prerequisites / 前置依赖**: A's outcome determines if B is needed / A 的结论决定 B 是否需要做
- **Coupled items / 强耦合项**: discuss together, may share a commit / 一起讨论方案，可合并提交
- **Independent items / 独立项**: can proceed quickly / 无依赖，快速推进

### Phase 4: Iterative Optimization Loop / 逐项优化循环

For each item: **propose → discuss → implement → review → commit → next**

对每项重复：**提出方案 → 讨论确认 → 实施修改 → 用户验收 → 提交 Git → 下一项**

Key behaviors / 关键行为:

- Always discuss before coding, especially UI/UX changes / 先讨论再动手，尤其是 UI/UX 变化
- Each item gets its own git commit / 每个优化项单独一个 commit
- Review phase actively solicits user feedback — this is where new discoveries happen most / 验收环节主动征询反馈 — 这是发现新问题的高频时刻
- New findings are formally appended to the checklist / 新发现必须作为正式编号条目追加到清单

### Phase 5: Summary / 收尾总结

Update checklist, run `git diff --stat` for code impact metrics, output summary table.

更新清单状态，统计代码改动量，输出总结表格。

## Design Principles (Built-in) / 内置设计原则

- Fewer visual layers is better (2 levels > 3 levels) / 视觉层级宜少不宜多
- Content over decoration (minimize borders, shadows, backgrounds) / 减少容器装饰，让内容成为主角
- No duplicate information on the same page / 同一信息不重复出现
- Inaccurate data is worse than no data / 展示不准确的数据比不展示更糟
- Arrange information by user decision priority / 信息排列遵循用户决策优先级
- Understand competitor design logic, don't copy surfaces / 理解竞品设计逻辑，不要表面照抄

## Requirements / 前置条件

- [Claude Code](https://docs.anthropic.com/en/docs/claude-code) CLI or IDE extension / CLI 或 IDE 扩展
- A project with git initialized / 已初始化 git 的项目

## License / 许可证

MIT
