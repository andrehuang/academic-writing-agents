# Academic Writing Principles (19)

Distilled from thesis supervisor + author self-review feedback (March 2026).
Canonical reference — all agents and workflows should consult this file.

---

## 1. Recursive Consistency Checks
For each chapter, section, and subsection — verify that terminology, section summary/intro, actual flow, and experiments all match. If a section says "we discuss X, Y, Z," the subsections must cover exactly X, Y, Z in that order.

**Common violations**: Section intro promises three topics but delivers two; subsection order doesn't match the intro's enumeration; terminology drifts between sections (e.g., "feature" vs "representation").

## 2. Logical Chaining with Transitions
Every paragraph, section, and chapter should be "chained" logically. The end of one section should motivate the start of the next. Never leave two adjacent paragraphs without a transition. Section-level transitions are necessary but insufficient — paragraph-to-paragraph connections are the more common failure mode.

**Common violations**: Abrupt topic shifts between paragraphs; sections that start with no connection to what came before; chapter endings that don't set up the next chapter; adjacent paragraphs on related subtopics connected only by thematic proximity rather than explicit bridging.

## 3. Math for Clarity, Not Complexity
Use formal notation to make difficult concepts precise when applicable, but theories should serve to *clarify*, not confuse or overwhelm. If notation doesn't add precision, drop it. Introduce no more than two new symbols per sentence. When a passage requires multiple definitions, space them across sentences with interleaving explanation.

**Common violations**: Introducing notation used only once; over-formalizing intuitive concepts; inconsistent symbol meanings across sections; multiple new symbols defined in a single sentence without intervening explanation.

## 4. Active Figure Use
Use figures to explain or illustrate complicated concepts. If a concept is hard to convey in text alone, create a figure. Consider whether every major chapter section has adequate visual support.

**Common violations**: Long stretches of dense text with no visual support; figures that decorate rather than explain; missing overview/pipeline figures for method sections.

## 5. Cross-Reference All Floats
Never let any figure or table "just be there." Every float must be explicitly referenced and discussed in the surrounding text.

**Common violations**: Figures placed in the document but never mentioned with \ref; tables referenced once without discussion of their content.

## 6. Figure-Text-Caption Consistency
Always match what the figure shows, what the caption says, and what the body text says. If they describe the same concept differently, reconcile them. If a figure places items in certain positions (e.g., a 2D plot), the text must match that placement.

**Common violations**: Caption describes elements not visible in the figure; body text says "top-left" when the item is bottom-right; caption and text use different terminology for the same element.

## 7. Avoid Exhaustive-Sounding Enumerations
When listing examples, use "such as" rather than "for" to avoid implying the list is complete. ("benchmarks for X, Y, Z" -> "benchmarks such as X, Y, Z")

**Common violations**: "for" used with partial lists; enumerations that imply completeness when the list is illustrative.

## 8. Avoid Negation-Contrast Structures
Rephrase "not X, but Y" / "not because... but because..." / "not that... but that..." positively. These are a strong AI-writing marker. E.g., "not because it is rarer, but because no one defined it" -> "because no one had conceptualized it as a category, regardless of how often it occurs."

**Common violations**: Sentences structured around negation before stating the actual point; double negatives; "not only... but also" used excessively.

## 9. Cite All Named Models/Benchmarks/Datasets
At first use in each section, even if cited earlier in the thesis. Readers may jump to individual sections.

**Common violations**: Named methods mentioned without citation after the first chapter; benchmark names used without references in experiment sections that readers may access directly.

## 10. One Figure, One Message
Do not layer multiple stories onto one visualization. If a figure answers two questions, consider splitting.

**Common violations**: Figures with too many subplots serving different arguments; a single figure trying to show both the method pipeline and the results.

## 11. Avoid Colloquial Terminology in Titles/Formal Claims
Vivid phrases can appear parenthetically but should not be primary terminology. Use formal terms in titles; introduce colloquial terms once parenthetically.

**Common violations**: Informal shorthand used as section titles; colloquial metaphors presented as formal definitions.

## 12. Match Discussion Tone to Thesis Voice
Discussion/findings should flow as analytical prose (claim -> evidence -> mechanism -> example -> principle), not flat report-style enumeration. The author's voice is deductive, first-person plural, active, with calibrated hedging. See the project CLAUDE.md for the full style profile.

**Common violations**: Bullet-point style findings; flat enumeration without analytical depth; discussion sections that read like lists rather than arguments.

## 13. Figure/Table Definition Order
Ensure that figure/table definition order in the source matches the order they are first mentioned and discussed in the text. Teaser figures may appear early but must still be discussed promptly.

**Common violations**: LaTeX source defines Figure 5 before Figure 3; a figure is \input'd early but not referenced until much later.

## 14. One Idea Per Sentence
Split sentences that pack multiple distinct claims (method + contrast + result). Each sentence should advance exactly one point. If a sentence needs "while", "unlike", or a semicolon to stitch together separate claims, it should be two sentences.

**Common violations**: Sentences with "unlike X which...", "while prior work does A, we do B and achieve C", or subordinate clauses introducing separate claims from the main clause; compound sentences where each half could stand alone as a distinct contribution.

## 15. Close Every Paragraph
The last sentence of a paragraph should conclude, synthesize, or motivate the next paragraph — not trail off. A strong closer draws an implication, states a principle, or poses a question the next paragraph answers.

**Common violations**: Paragraphs ending with "subsequently", "which we detail below", or a bare citation; final sentences that introduce new information without resolution; paragraphs that simply stop after the last piece of evidence.

## 16. Claim-First Exposition
State the conceptual contribution or objective before diving into technical details. The reader should know *what* and *why* before *how*. The first 1–2 sentences of each section or subsection should declare the goal before presenting formulas or procedures.

**Common violations**: Sections that open with equations or implementation details before stating the purpose; subsections that dive into "how" without first explaining "what" or "why"; method descriptions that defer the motivation to the end.

## 17. Calibrated Confidence Language
Use assertive language for empirical facts ("achieves", "outperforms", "yields") and hedged language for causal explanations ("we observe", "we hypothesize", "this suggests"). Do not hedge facts or assert mechanisms.

**Common violations**: "because" / "due to" / "leads to" used with assertive tone for unproven causal mechanisms; "may" / "might" / "could" modifying reported numerical results; mixing confidence levels within the same sentence.

## 18. Interpret Figures, Don't Just Reference
When referencing a figure, tell the reader what to look for. Not just "as shown in Figure X" — say what the figure reveals, what pattern to notice, or what comparison matters. This extends principle 5 (which checks existence of reference; this checks quality of reference).

**Common violations**: Bare "see Figure X" or "as shown in Figure X" without interpretive guidance; figure references that state the figure exists but not what it demonstrates; paragraphs that rely on the reader to independently extract the figure's message.

## 19. Strategic Limitation Placement
How and where to discuss limitations depends on the document type. **Peer-reviewed papers**: Be strategic — don't expose weaknesses prematurely. Options: (a) acknowledge briefly with a potential fix ("While X assumes Y, this can be mitigated by Z"), (b) place in a dedicated limitations section after results build confidence, (c) frame as future work rather than weakness. **Thesis / internal documents**: Discuss limitations earlier and more clearly, at the point the design decision is made, so the reader (supervisor, committee) sees the author's awareness of assumptions and tradeoffs.

**Common violations**: Limitations mentioned in the method section of a paper before the reader has seen results; limitations omitted entirely from a thesis chapter; limitations listed without mitigation or context; defensive tone when discussing known constraints.

## 20. Figure Row Alignment
Use `[t]` alignment on subfigures in multi-row grids to ensure rows align at their tops. When subfigures in a row have different heights (e.g., one has a caption and others do not, or one is a PNG and others are PDFs), `[b]` alignment causes visual misalignment. Add explicit height constraints (`\includegraphics[height=X]`) when images within a row have different aspect ratios.

**Common violations**: Using `[b]` alignment in subfigure grids (the default in many templates); rows where captions appear only on some subfigures, pushing others up or down; mixing raster and vector formats without height normalization.

## 21. Citation Completeness at First Mention
Cite foundational methods and models (SIFT, HOG, CNN/AlexNet, Transformer, etc.) at their first mention in each chapter, even if they are well-known. Readers may start from any chapter; a bare mention without citation forces them to search for the reference.

**Common violations**: Named methods mentioned without citation after their first appearance in Ch. 1; acronyms like "CNN" or "ViT" used without a citation in chapters that readers may access independently; benchmark names (ImageNet, COCO) used without references in experiment sections.

## 22. Negation-Contrast Audit
Before finalizing any chapter, search for "not...but" patterns and rephrase positively. Negation-contrast structures ("not X, but Y") are a strong AI-writing marker per Principle 8. A final-pass grep for patterns like `is not.*but`, `not to.*but to`, `not how.*but` catches residual instances.

**Common violations**: Sentences structured as "the question is not X but Y" (rephrase: "the question is Y"); "the goal is not to X but to Y" (rephrase: "the goal is to Y: ..."); "not only...but also" used to combine two claims that should be separate sentences.
