# Academic Writing Agents

A [Claude Code plugin](https://docs.anthropic.com/en/docs/claude-code/plugins) that brings multi-agent review to academic writing — the same "multiple expert reviewers" model that makes peer review work, built into your writing process.

## Why

The gap between doing great research and writing about it clearly costs real impact. Findings get buried in unclear prose, reviewers stumble over notation inconsistencies, and figures fail to carry their weight. Most researchers get feedback from one or two people, often late in the process.

This plugin gives you a team of 12 specialist agents — each focused on a different dimension of writing quality — working in parallel, available at any point in the writing process.

## Design Philosophy

Informed by Michael Black's "Writing a Good Scientific Paper" and real thesis/paper writing experience:

- **Parallel expert review.** Multiple specialized agents review simultaneously, each catching what others miss — like having a writing coach, a technical reviewer, a figure specialist, and a bibliography checker all reading at once.
- **Review-then-act.** Always diagnose before fixing. The writing-reviewer identifies issues; the prose-polisher implements fixes. Never blindly edit.
- **30 codified principles.** Not ad-hoc corrections but a systematic framework organized into 6 categories: Structure & Narrative, Prose & Style, Math & Equations, Figures & Tables, Citations & Bibliography, and Process & Meta.
- **Human-in-the-loop.** Agents propose; humans decide. The plugin presents a prioritized plan and the author chooses what to act on.
- **Goal-Problem-Solution rhythm.** From Black's guide — every section should follow the GPS pattern. The plugin itself is structured this way: identify what you want to improve (goal), diagnose what's wrong (problem), deploy the right agents to fix it (solution).

## How It Works

1. **Auto-triggers** when Claude detects academic writing context (`.tex` files, thesis chapters, paper drafts).
2. The `academic` skill reads project conventions from your `.claude/CLAUDE.md`.
3. Deploys the right specialist agents in parallel.
4. Synthesizes findings into a prioritized report (Critical / Important / Minor).
5. Offers to fix issues via action agents or direct edits.
6. Iterates with you until you're satisfied.

You can also invoke it manually: `/academic review my introduction`.

## What's Included

### Skill

| Skill | Command | Description |
|-------|---------|-------------|
| **Academic** | `/academic <task>` | Orchestrates specialist agents for academic writing tasks |

### Agents (12 total)

**Review Agents** (read-only analysis):

| Agent | Focus |
|-------|-------|
| `consistency-checker` | Terminology, cross-refs, figure-text-caption alignment, structural coherence |
| `logic-reviewer` | Argument flow, transitions, narrative arc, logical gaps |
| `technical-reviewer` | Math notation, methodology, results validity, citations |
| `writing-reviewer` | Prose clarity, conciseness, grammar, academic tone |
| `latex-layout-auditor` | PDF layout audit — float placement, alignment, sizing |

**Audit Agents** (read + verify):

| Agent | Focus |
|-------|-------|
| `bibliography-auditor` | Bib entry completeness, arXiv updates, title capitalization, venue consistency |

**Research Agents** (read + web):

| Agent | Focus |
|-------|-------|
| `research-analyst` | Related work, novelty assessment, positioning, gap analysis |
| `brainstormer` | Alternative framings, cross-disciplinary connections, research directions |

**Survey Agents** (read + web + write):

| Agent | Focus |
|-------|-------|
| `paper-crawler` | Collects papers from DBLP + OpenAlex APIs, deduplicates, classifies |

**Action Agents** (read + write):

| Agent | Focus |
|-------|-------|
| `prose-polisher` | Rewrites text for clarity, conciseness, flow (edits, not just reports) |
| `section-drafter` | Drafts LaTeX sections, paragraphs, transitions, captions, abstracts |
| `latex-figure-specialist` | Creates/adjusts TikZ/pgfplots figures, manages placement and layout |

### 30 Principles

Organized into 6 categories:

**A. Structure & Narrative** — A1 Recursive Consistency, A2 Logical Chaining, A3 Definition Order, A4 Paragraph Closers, A5 Claim-First, A6 GPS Rhythm, A7 The Nugget

**B. Prose & Style** — B1 Enumerations, B2 Negation-Contrast, B3 Colloquial Terms, B4 Thesis Voice, B5 One Idea/Sentence, B6 Calibrated Confidence, B7 Ruthless Conciseness, B8 AI-Tell Detection

**C. Math & Equations** — C1 Math for Clarity, C2 Triple Explanation, C3 Equation-Code Correspondence

**D. Figures & Tables** — D1 Active Figures, D2 Cross-Reference Floats, D3 Figure-Text-Caption Consistency, D4 One Message, D5 Interpret Figures, D6 Row Alignment, D7 Caption Self-Sufficiency

**E. Citations & Bibliography** — E1 Cite Named Entities, E2 Citation Completeness, E3 Bibliography Hygiene

**F. Process & Meta** — F1 Strategic Limitations, F2 Negation-Contrast Audit

## Usage

The plugin **auto-triggers** when Claude detects academic writing context — `.tex` files, thesis chapters, paper drafts, bibliography work. Just describe what you need in natural language:

```
Review chapter 3 for consistency and technical correctness

Draft a transition paragraph from the method section to experiments

Polish the abstract in parts/abstract.tex

Audit the bibliography for missing fields and arXiv updates

How does our approach compare to recent test-time adaptation papers?

Survey recent work on test-time adaptation from top venues 2023–2025

Plan the structure for a related work section on domain generalization

Prepare this paper for NeurIPS submission — full review pipeline
```

You can also invoke the skill explicitly with `/academic <task>` if auto-triggering doesn't activate.

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

## Customization

### Project-level agents

Add domain-specific agents to your project's `.claude/agents/` directory. The plugin auto-discovers them and includes them in deployment plans.

### Project-level conventions

Add a `.claude/CLAUDE.md` to your project with:
- Document structure (chapters, files, build commands)
- LaTeX conventions (macros, figure paths, citation style)
- Author writing style profile (voice, tone, patterns to match)

All agents read this before starting, so they adapt to your project's specific conventions.

### Extending the agent roster

Add new agents to `~/.claude/agents/` (global) or `<project>/.claude/agents/` (project-level). Each agent is a Markdown file with YAML frontmatter specifying name, description, tools, and model. The plugin picks them up automatically.

## Acknowledgments

The principles and workflows in this plugin draw on:
- Michael Black's "Writing a Good Scientific Paper" — the GPS rhythm, the nugget concept, and the emphasis on figures as first-class citizens
- Real thesis supervision experience — patterns observed across multiple rounds of advisor feedback
- Peer review experience — what reviewers actually flag and what they miss

## License

MIT
