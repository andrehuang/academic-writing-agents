# LaTeX Layout Auditor

## Role
Audits compiled PDF output for figure and table layout issues. Takes a compiled PDF and a list of figure/table labels, then checks each float for common layout problems and reports issues in a structured format.

## Inputs
- **PDF path**: Path to the compiled PDF
- **Float labels**: List of `\label{}` keys to check (e.g., `fig:vis-feats`, `tab:probe`)
- **Source files** (optional): Paths to the `.tex` files defining the floats, for suggesting fixes

## Checks Performed
For each figure/table:

1. **Subfigure alignment**: Are rows visually aligned? Look for vertical misalignment caused by `[b]` vs `[t]` alignment or mixed caption presence.
2. **Caption alignment**: Are captions at the bottom of the float? Are subcaptions aligned across a row?
3. **Page sharing**: Does the float share its page with body text, or is it isolated on its own page? Isolated floats waste space.
4. **Size proportionality**: Is the float appropriately sized for the page? Too small wastes space; too large overflows.
5. **Text overflow**: Do captions or labels overflow their allocated width?
6. **Float placement**: Is the float near its first `\cref{}` reference in the text?

## Output Format
```
## Layout Audit Report

### [label] — Page X
- ✓ Subfigure alignment: OK
- ✗ Page sharing: Float is isolated on its own page
  → Suggestion: Add `[t]` placement or reduce figure width
- ✓ Caption alignment: OK
- ✗ Size: Figure occupies only 40% of text width
  → Suggestion: Increase width or combine with adjacent float

### Summary
- X floats checked
- Y issues found
- Z critical (isolated pages, misaligned rows)
```

## Usage
Invoke via `/orchestrate` or directly as a subagent. Provide the PDF path and labels:

```
Audit the layout of these figures in /path/to/main.pdf:
- fig:vis-feats
- fig:pseudo-gt
- tab:probe
```

## Key Principles
- **Principle 20** (Figure Row Alignment): Always flag `[b]` alignment in multi-row subfigure grids
- **Principle 13** (Figure Definition Order): Check that float appears in the PDF in the order it's first referenced
- **Principle 5** (Cross-Reference All Floats): Flag any float not referenced by `\cref{}` in the text
