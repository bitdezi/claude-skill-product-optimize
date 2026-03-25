# product-optimize

A Claude Code skill for systematic product optimization — discover issues, document checklist, analyze dependencies, then iteratively discuss, implement, review, and commit.

Claude Code 自定义 Skill，用于系统性产品优化：发现问题 → 记录清单 → 依赖分析 → 逐项（讨论 → 实施 → 验收 → 提交）。

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
/product-optimize 用户设置页
/product-optimize checkout flow
```

## What It Does / 功能介绍

The skill guides Claude through a structured 5-phase optimization workflow:

该 Skill 引导 Claude 执行结构化的 5 阶段优化流程：

### Phase 1: Discovery / 第一阶段：发现问题

Examine the target code with fresh eyes across 4 dimensions:

以全新视角审视目标代码，从 4 个维度识别优化点：

- **Visual & UX / 视觉与体验**: hierarchy, information architecture, consistency, responsiveness / 视觉层级、信息架构、组件一致性、响应式
- **Data & Logic / 数据与逻辑**: accuracy, edge cases, consistency / 数据准确性、边界情况、一致性
- **Code Quality / 代码质量**: anti-patterns, hardcoded values, reuse opportunities / 反模式、硬编码值、复用机会
- **Competitive Reference / 竞品参考**: how similar products solve the same problem / 同类产品的设计逻辑

### Phase 2: Checklist / 第二阶段：记录清单

Create a structured optimization checklist document with status tracking.

创建结构化的优化清单文档，包含现状、目标、状态追踪。

### Phase 3: Dependency Analysis / 第三阶段：依赖分析

Analyze relationships between items to determine optimal execution order:

分析优化项之间的依赖关系，确定最优执行顺序：

- **Prerequisites / 前置依赖**: A's outcome determines if B is needed / A 的结论决定 B 是否需要做
- **Coupled items / 强耦合项**: discuss together, may share a commit / 一起讨论方案，可合并提交
- **Independent items / 独立项**: can proceed quickly / 无依赖，快速推进

### Phase 4: Iterative Optimization Loop / 第四阶段：逐项优化循环

For each item: **propose → discuss → implement → review → commit → next**

对每项重复：**提出方案 → 讨论确认 → 实施修改 → 用户验收 → 提交 Git → 下一项**

Key behaviors / 关键行为:

- Always discuss before coding, especially UI/UX changes / 先讨论再动手，尤其是 UI/UX 变化
- Each item gets its own git commit / 每个优化项单独一个 commit
- Review phase actively solicits user feedback — this is where new discoveries happen most / 验收环节主动征询反馈 — 这是发现新问题的高频时刻
- New findings are formally appended to the checklist / 新发现必须作为正式编号条目追加到清单

### Phase 5: Summary / 第五阶段：收尾总结

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
