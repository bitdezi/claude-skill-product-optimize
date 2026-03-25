# product-optimize

A Claude Code skill for systematic product optimization — discover issues, document checklist, analyze dependencies, then iteratively discuss, implement, review, and commit.

一个 Claude Code 自定义 Skill，用于系统性产品优化：发现问题 → 记录清单 → 依赖分析 → 逐项（讨论 → 实施 → 验收 → 提交）。

## Installation

```bash
cp SKILL.md ~/.claude/skills/product-optimize/SKILL.md
```

Or clone and link:

```bash
git clone https://github.com/YOUR_USERNAME/claude-skill-product-optimize.git
mkdir -p ~/.claude/skills/product-optimize
cp claude-skill-product-optimize/SKILL.md ~/.claude/skills/product-optimize/
```

## Usage

In Claude Code, invoke the skill with:

```
/product-optimize <target description>
```

Examples:

```
/product-optimize token detail page trade panel
/product-optimize user settings page
/product-optimize checkout flow
```

## What It Does

The skill guides Claude through a structured 5-phase optimization workflow:

### Phase 1: Discovery
Examine the target code with fresh eyes across 4 dimensions:
- **Visual & UX**: hierarchy, information architecture, consistency, responsiveness
- **Data & Logic**: accuracy, edge cases, consistency
- **Code Quality**: anti-patterns, hardcoded values, reuse opportunities
- **Competitive Reference**: how similar products solve the same problem

### Phase 2: Checklist
Create a structured optimization checklist document with status tracking.

### Phase 3: Dependency Analysis
Analyze relationships between items to determine optimal execution order:
- **Prerequisites**: A's outcome determines if B is needed
- **Coupled items**: discuss together, may share a commit
- **Independent items**: can proceed quickly

### Phase 4: Iterative Optimization Loop
For each item: **propose → discuss → implement → review → commit → next**

Key behaviors:
- Always discuss before coding (especially UI/UX changes)
- Each item gets its own git commit
- Review phase actively solicits user feedback — this is where new discoveries happen most
- New findings are formally appended to the checklist

### Phase 5: Summary
- Update checklist, run `git diff --stat` for code impact metrics, output summary table.

## Design Principles (Built-in)

- Fewer visual layers is better (2 levels > 3 levels)
- Content over decoration (minimize borders, shadows, backgrounds)
- No duplicate information on the same page
- Inaccurate data is worse than no data
- Arrange information by user decision priority
- Understand competitor design logic, don't copy surfaces

## Requirements

- [Claude Code](https://docs.anthropic.com/en/docs/claude-code) CLI or IDE extension
- A project with git initialized

## License

MIT
