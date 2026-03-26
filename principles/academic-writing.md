# Academic Writing Principles (30)

Distilled from thesis supervision, author self-review feedback, and Michael Black's "Writing a Good Scientific Paper" (March 2026).
Canonical reference — all agents and workflows should consult this file.
Organized into 6 categories that map to agent specializations.

---

## A. Structure & Narrative

*Primary agents: logic-reviewer, consistency-checker*

### A1. Recursive Consistency Checks
For each chapter, section, and subsection — verify that terminology, section summary/intro, actual flow, and experiments all match. If a section says "we discuss X, Y, Z," the subsections must cover exactly X, Y, Z in that order.

**Common violations**: Section intro promises three topics but delivers two; subsection order doesn't match the intro's enumeration; terminology drifts between sections (e.g., "feature" vs "representation").

### A2. Logical Chaining with Transitions
Every paragraph, section, and chapter should be "chained" logically. The end of one section should motivate the start of the next. Never leave two adjacent paragraphs without a transition. Section-level transitions are necessary but insufficient — paragraph-to-paragraph connections are the more common failure mode.

**Common violations**: Abrupt topic shifts between paragraphs; sections that start with no connection to what came before; chapter endings that don't set up the next chapter; adjacent paragraphs on related subtopics connected only by thematic proximity rather than explicit bridging.

### A3. Figure/Table Definition Order
Ensure that figure/table definition order in the source matches the order they are first mentioned and discussed in the text. Teaser figures may appear early but must still be discussed promptly.

**Common violations**: LaTeX source defines Figure 5 before Figure 3; a figure is \input'd early but not referenced until much later.

### A4. Close Every Paragraph
The last sentence of a paragraph should conclude, synthesize, or motivate the next paragraph — not trail off. A strong closer draws an implication, states a principle, or poses a question the next paragraph answers.

**Common violations**: Paragraphs ending with "subsequently", "which we detail below", or a bare citation; final sentences that introduce new information without resolution; paragraphs that simply stop after the last piece of evidence.

### A5. Claim-First Exposition
State the conceptual contribution or objective before diving into technical details. The reader should know *what* and *why* before *how*. The first 1–2 sentences of each section or subsection should declare the goal before presenting formulas or procedures.

**Common violations**: Sections that open with equations or implementation details before stating the purpose; subsections that dive into "how" without first explaining "what" or "why"; method descriptions that defer the motivation to the end.

### A6. Goal-Problem-Solution Rhythm
Every section — from the full paper down to individual subsections — should follow a Goal-Problem-Solution (GPS) rhythm. **Goal**: what are we trying to achieve? **Problem**: what makes this hard or what's missing? **Solution**: how do we address it? This rhythm gives the reader a reason to care before presenting the technical content. Sections that jump to solutions without establishing the goal and problem lose the reader's motivation.

**Common violations**: Method sections that present techniques without first stating what problem each technique solves; introduction paragraphs that list contributions without establishing the gap; subsections that describe "how" without "why this is needed."

### A7. The Nugget — One Key Insight Per Paper
Every paper should orbit a single key insight — the "nugget" — that the reader takes away. All sections, experiments, and figures should serve this central message. If you cannot state the nugget in one sentence, the paper's focus is unclear. The nugget is not the method; it is the insight that makes the method work or the finding that changes how we think about the problem.

**Common violations**: Papers that present multiple loosely connected contributions without a unifying insight; abstracts that list techniques rather than stating what was learned; conclusion sections that enumerate results rather than crystallizing the takeaway.

---

## B. Prose & Style

*Primary agents: writing-reviewer, prose-polisher*

### B1. Avoid Exhaustive-Sounding Enumerations
When listing examples, use "such as" rather than "for" to avoid implying the list is complete. ("benchmarks for X, Y, Z" -> "benchmarks such as X, Y, Z")

**Common violations**: "for" used with partial lists; enumerations that imply completeness when the list is illustrative.

### B2. Avoid Negation-Contrast Structures
Rephrase "not X, but Y" / "not because... but because..." / "not that... but that..." positively. These are a strong AI-writing marker. E.g., "not because it is rarer, but because no one defined it" -> "because no one had conceptualized it as a category, regardless of how often it occurs."

**Common violations**: Sentences structured around negation before stating the actual point; double negatives; "not only... but also" used excessively.

### B3. Avoid Colloquial Terminology in Titles/Formal Claims
Vivid phrases can appear parenthetically but should not be primary terminology. Use formal terms in titles; introduce colloquial terms once parenthetically.

**Common violations**: Informal shorthand used as section titles; colloquial metaphors presented as formal definitions.

### B4. Match Discussion Tone to Thesis Voice
Discussion/findings should flow as analytical prose (claim -> evidence -> mechanism -> example -> principle), not flat report-style enumeration. The author's voice is deductive, first-person plural, active, with calibrated hedging. See the project CLAUDE.md for the full style profile.

**Common violations**: Bullet-point style findings; flat enumeration without analytical depth; discussion sections that read like lists rather than arguments.

### B5. One Idea Per Sentence
Split sentences that pack multiple distinct claims (method + contrast + result). Each sentence should advance exactly one point. If a sentence needs "while", "unlike", or a semicolon to stitch together separate claims, it should be two sentences.

**Common violations**: Sentences with "unlike X which...", "while prior work does A, we do B and achieve C", or subordinate clauses introducing separate claims from the main clause; compound sentences where each half could stand alone as a distinct contribution.

### B6. Calibrated Confidence Language
Use assertive language for empirical facts ("achieves", "outperforms", "yields") and hedged language for causal explanations ("we observe", "we hypothesize", "this suggests"). Do not hedge facts or assert mechanisms.

**Common violations**: "because" / "due to" / "leads to" used with assertive tone for unproven causal mechanisms; "may" / "might" / "could" modifying reported numerical results; mixing confidence levels within the same sentence.

### B7. Ruthless Conciseness
Every word must earn its place. Academic writing is not about sounding sophisticated — it is about communicating precisely with minimal friction. Cut filler phrases ("it is important to note that", "in the context of"), compress relative clauses into participles or appositives, and prefer short Anglo-Saxon words over long Latinate ones when meaning is preserved ("use" not "utilize", "show" not "demonstrate"). A paragraph that says in 100 words what could be said in 60 is not thorough — it is wasteful.

**Common violations**: "It is worth noting that" (cut entirely); "in order to" -> "to"; "a large number of" -> "many"; "due to the fact that" -> "because"; "plays an important role in" -> "affects"; padding sentences with "importantly", "interestingly", "notably" as openers; restating in the conclusion what was already said in the abstract and introduction with only cosmetic changes.

### B8. AI-Writing Tell Detection
Actively scan for and eliminate patterns that mark text as AI-generated. Common tells: (1) "not X, but Y" negation-contrast (see B2), (2) "delve", "leverage", "landscape", "tapestry", "multifaceted", "paradigm shift", (3) sentences starting with "Moreover", "Furthermore", "Additionally" in sequence, (4) formulaic transitions ("Building on this", "Taking this a step further"), (5) hollow intensifiers ("crucial", "vital", "essential" used interchangeably), (6) mirroring the user's exact phrasing back, (7) overly balanced "on one hand / on the other hand" structures. Replace with direct, specific language.

**Common violations**: Three consecutive paragraphs starting with "Moreover" / "Furthermore" / "Additionally"; using "delve into" instead of "examine" or "analyze"; "leverage" as a verb when "use" suffices; "the landscape of X" as a vague framing; sentences that begin with a gerund phrase restating the previous sentence ("Building on the above analysis, we...").

---

## C. Math & Equations

*Primary agents: technical-reviewer*

### C1. Math for Clarity, Not Complexity
Use formal notation to make difficult concepts precise when applicable, but theories should serve to *clarify*, not confuse or overwhelm. If notation doesn't add precision, drop it. Introduce no more than two new symbols per sentence. When a passage requires multiple definitions, space them across sentences with interleaving explanation.

**Common violations**: Introducing notation used only once; over-formalizing intuitive concepts; inconsistent symbol meanings across sections; multiple new symbols defined in a single sentence without intervening explanation.

### C2. Triple Explanation — Text, Equation, Figure
Key concepts deserve explanation through all three modalities: intuitive text, formal equation, and visual figure. The text gives the reader intuition and motivation. The equation makes it precise. The figure makes it concrete and memorable. Not every concept needs all three, but any concept central to the paper's contribution should have at least two, and the core idea should have all three. The three explanations should reinforce each other, not merely repeat.

**Common violations**: Core methods described only via equations with no intuitive text; figures that illustrate the pipeline but not the key mathematical insight; text that paraphrases an equation without adding intuition; methods explained in text and equations but with no figure to ground the reader's understanding.

### C3. Equation-Code Correspondence
When a paper presents both mathematical formulations and implementation details (pseudocode, algorithm blocks, or references to released code), the notation should map clearly to the implementation. Variable names in equations should correspond to variable names in code or pseudocode. If the mapping is non-trivial, state it explicitly. Readers who want to implement the method should not need to reverse-engineer the connection.

**Common violations**: Equations using $\alpha$ and $\beta$ while pseudocode uses `lr` and `momentum` without mapping; algorithm blocks that introduce new variable names not present in the mathematical formulation; loss functions defined differently in the equation and the code; dimension ordering (e.g., batch-first vs channel-first) differing between equations and implementation without comment.

---

## D. Figures & Tables

*Primary agents: consistency-checker, latex-layout-auditor, latex-figure-specialist*

### D1. Active Figure Use
Use figures to explain or illustrate complicated concepts. If a concept is hard to convey in text alone, create a figure. Consider whether every major chapter section has adequate visual support.

**Common violations**: Long stretches of dense text with no visual support; figures that decorate rather than explain; missing overview/pipeline figures for method sections.

### D2. Cross-Reference All Floats
Never let any figure or table "just be there." Every float must be explicitly referenced and discussed in the surrounding text.

**Common violations**: Figures placed in the document but never mentioned with \ref; tables referenced once without discussion of their content.

### D3. Figure-Text-Caption Consistency
Always match what the figure shows, what the caption says, and what the body text says. If they describe the same concept differently, reconcile them. If a figure places items in certain positions (e.g., a 2D plot), the text must match that placement.

**Common violations**: Caption describes elements not visible in the figure; body text says "top-left" when the item is bottom-right; caption and text use different terminology for the same element.

### D4. One Figure, One Message
Do not layer multiple stories onto one visualization. If a figure answers two questions, consider splitting.

**Common violations**: Figures with too many subplots serving different arguments; a single figure trying to show both the method pipeline and the results.

### D5. Interpret Figures, Don't Just Reference
When referencing a figure, tell the reader what to look for. Not just "as shown in Figure X" — say what the figure reveals, what pattern to notice, or what comparison matters. This extends principle D2 (which checks existence of reference; this checks quality of reference).

**Common violations**: Bare "see Figure X" or "as shown in Figure X" without interpretive guidance; figure references that state the figure exists but not what it demonstrates; paragraphs that rely on the reader to independently extract the figure's message.

### D6. Figure Row Alignment
Use `[t]` alignment on subfigures in multi-row grids to ensure rows align at their tops. When subfigures in a row have different heights (e.g., one has a caption and others do not, or one is a PNG and others are PDFs), `[b]` alignment causes visual misalignment. Add explicit height constraints (`\includegraphics[height=X]`) when images within a row have different aspect ratios.

**Common violations**: Using `[b]` alignment in subfigure grids (the default in many templates); rows where captions appear only on some subfigures, pushing others up or down; mixing raster and vector formats without height normalization.

### D7. Figure Caption Self-Sufficiency
A caption should be understandable without reading the body text. It should state what the figure shows, define any abbreviations or symbols used in the figure, and highlight the key takeaway. Readers often scan figures and captions before deciding whether to read the full text — the caption is the figure's elevator pitch.

**Common violations**: Captions that say only "Results on dataset X" without explaining what the axes, colors, or groups represent; captions that reference terms defined only in the body text; captions that describe the visual layout ("Left: ..., Right: ...") without stating the message; captions missing units on reported quantities.

---

## E. Citations & Bibliography

*Primary agents: technical-reviewer, bibliography-auditor*

### E1. Cite All Named Models/Benchmarks/Datasets
At first use in each section, even if cited earlier in the thesis. Readers may jump to individual sections.

**Common violations**: Named methods mentioned without citation after the first chapter; benchmark names used without references in experiment sections that readers may access directly.

### E2. Citation Completeness at First Mention
Cite foundational methods and models (SIFT, HOG, CNN/AlexNet, Transformer, etc.) at their first mention in each chapter, even if they are well-known. Readers may start from any chapter; a bare mention without citation forces them to search for the reference.

**Common violations**: Named methods mentioned without citation after their first appearance in Ch. 1; acronyms like "CNN" or "ViT" used without a citation in chapters that readers may access independently; benchmark names (ImageNet, COCO) used without references in experiment sections.

### E3. Bibliography Hygiene
Bibliography entries should be complete, consistent, and up-to-date. Check: (1) every entry has the required fields for its type (authors, title, year, venue/journal, pages, DOI where available), (2) title capitalization is protected with braces for proper nouns and acronyms (e.g., `{ImageNet}`, `{BERT}`), (3) arXiv-only citations are updated to their published versions when available, (4) author names are consistent across entries (not "Vaswani, A." in one and "Ashish Vaswani" in another), (5) venue names are consistent (not "NeurIPS" in one entry and "Advances in Neural Information Processing Systems" in another — pick one style), (6) no "?" markers appear in the compiled PDF (indicating unresolved references). Run `biber --validate-datamodel` or check the .blg file for warnings.

**Common violations**: arXiv preprints cited when a published version exists at a top venue; missing page numbers or DOIs; inconsistent venue abbreviations; title-cased titles without brace protection causing lowercase output; duplicate bib entries under different keys; entries with placeholder fields ("to appear", "forthcoming") that were never updated.

---

## F. Process & Meta

*Primary agents: writing-reviewer (final pass)*

### F1. Strategic Limitation Placement
How and where to discuss limitations depends on the document type. **Peer-reviewed papers**: Be strategic — don't expose weaknesses prematurely. Options: (a) acknowledge briefly with a potential fix ("While X assumes Y, this can be mitigated by Z"), (b) place in a dedicated limitations section after results build confidence, (c) frame as future work rather than weakness. **Thesis / internal documents**: Discuss limitations earlier and more clearly, at the point the design decision is made, so the reader (supervisor, committee) sees the author's awareness of assumptions and tradeoffs.

**Common violations**: Limitations mentioned in the method section of a paper before the reader has seen results; limitations omitted entirely from a thesis chapter; limitations listed without mitigation or context; defensive tone when discussing known constraints.

### F2. Negation-Contrast Audit
Before finalizing any chapter, search for "not...but" patterns and rephrase positively. Negation-contrast structures ("not X, but Y") are a strong AI-writing marker per Principle B2. A final-pass grep for patterns like `is not.*but`, `not to.*but to`, `not how.*but` catches residual instances.

**Common violations**: Sentences structured as "the question is not X but Y" (rephrase: "the question is Y"); "the goal is not to X but to Y" (rephrase: "the goal is to Y: ..."); "not only...but also" used to combine two claims that should be separate sentences.
