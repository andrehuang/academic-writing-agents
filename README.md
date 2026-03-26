# Academic Writing Agents

A [Claude Code plugin](https://docs.anthropic.com/en/docs/claude-code/plugins) providing a multi-agent orchestrator for academic writing. 11 specialist agents handle review, research, literature surveys, drafting, polishing, and figure work — all coordinated through a single `/orchestrate` command.

## What's included

### Skill (slash command)

| Skill | Command | Description |
|-------|---------|-------------|
| **Orchestrate** | `/orchestrate <task>` | Deploys specialist agents in parallel, synthesizes results, drives iterative improvement |

### Agents (deployed by the orchestrator)

**Review agents** (read-only analysis):
- `consistency-checker` — Terminology, cross-refs, figure-text-caption alignment
- `logic-reviewer` — Argument flow, transitions, narrative arc
- `technical-reviewer` — Math, methodology, results validity, citations
- `writing-reviewer` — Prose clarity, conciseness, grammar, tone
- `latex-layout-auditor` — PDF layout audit (figures, tables, alignment)

**Research agents** (read + web):
- `research-analyst` — Related work, novelty, positioning, gap analysis
- `brainstormer` — Creative ideas, alternative framings, research directions

**Survey agents** (read + web + write):
- `paper-crawler` — Collects papers from DBLP + OpenAlex APIs, deduplicates, optionally classifies

**Action agents** (read + write):
- `prose-polisher` — Rewrites text for clarity and flow
- `section-drafter` — Drafts LaTeX sections, paragraphs, transitions, captions
- `latex-figure-specialist` — Creates/adjusts TikZ/pgfplots figures

### Principles

`academic-writing.md` — 19 principles for academic writing (consistency checks, logical chaining, math clarity, active figures, etc.), referenced by all agents.

## Installation

```bash
# Install from the marketplace:
claude plugin install andrehuang-academic-writing-agents

# Or install directly from GitHub:
claude plugin install --url https://github.com/andrehuang/academic-writing-agents
```

Or test locally during development:
```bash
claude --plugin-dir /path/to/academic-writing-agents
```

## Usage

Everything goes through `/orchestrate`:

```bash
# Full chapter review (deploys 4 reviewers in parallel)
/orchestrate review parts/chapter3.tex

# Draft a new section
/orchestrate draft a transition paragraph from the method section to experiments

# Polish existing text
/orchestrate polish the abstract in parts/abstract.tex

# Research positioning
/orchestrate analyze how our approach compares to recent test-time adaptation papers

# Collect papers for a literature survey
/orchestrate collect papers on domain generalization --venues NeurIPS,ICML,ICLR --years 2023-2025

# Full literature survey pipeline (collect + analyze)
/orchestrate survey recent work on test-time adaptation from top venues
```

## Customization

### Project-level agents

Add domain-specific agents to your project's `.claude/agents/` directory. The orchestrator auto-discovers them and includes them in deployment plans.

### Project-level conventions

Add a `.claude/CLAUDE.md` to your project with structure, LaTeX conventions, and writing style. All agents read this before starting.

## License

MIT
