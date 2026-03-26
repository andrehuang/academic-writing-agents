---
name: paper-crawl
description: Collect and classify research papers from DBLP and OpenAlex APIs
user_invocable: true
---

# Paper Crawl

Collect research papers on a given topic from academic APIs, deduplicate, and optionally classify them using an LLM.

## Usage

```
/paper-crawl <topic> [--venues VENUE1,VENUE2,...] [--years 2022-2025] [--classify]
```

## Behavior

When invoked, follow these steps:

### Step 1: Parse input

Extract from the user's message:
- **Topic**: the research area to search (e.g., "domain generalization", "test-time adaptation")
- **Venues** (optional): comma-separated venue names to search (default: NeurIPS, ICML, ICLR, CVPR, ICCV, ECCV)
- **Years** (optional): year range (default: 2022-2025)
- **Classify** (optional): whether to classify papers after collection

### Step 2: Build query templates

Generate query strings by combining the topic with venue-year pairs:
```
"{venue} {year} {topic}"
```

For broad topics, also generate variant queries:
- The user's exact topic phrase
- Closely related phrasings (e.g., "domain generalization" -> also "domain shift", "distribution shift")

### Step 3: Query APIs

Query **both** APIs for each query string (no auth needed for either):

#### DBLP API
```
GET https://dblp.org/search/publ/api?q={query}&format=json&h=100
```
Extract: title, venue, year, authors, DOI/URL from `result.hits.hit[].info`

#### OpenAlex API
```
GET https://api.openalex.org/works?search={query}&filter=publication_year:{year}&per_page=100
```
Extract: title, venue (host_venue.display_name), year, abstract (from abstract_inverted_index), DOI

**Rate limits**: DBLP allows ~1 req/sec. OpenAlex allows 10 req/sec unauthenticated (be polite, use 2 req/sec).

### Step 4: Deduplicate

Normalize titles (lowercase, strip non-alphanumeric) and deduplicate across all queries and both APIs.

### Step 5: Output

Write results to `papers.json` in the current directory:
```json
[
  {
    "title": "...",
    "authors": ["..."],
    "venue": "...",
    "year": 2024,
    "abstract": "...",
    "url": "...",
    "source_api": "dblp|openalex",
    "source_query": "..."
  }
]
```

Report summary: total papers found, per-venue counts, per-year counts.

### Step 6 (optional): Classify

If `--classify` is specified, classify each paper along these dimensions using the LLM:

1. **Relevance** (yes/no): Is this paper actually about the target topic?
2. **Contribution type**: method / analysis / benchmark / survey
3. **Brief summary**: 1-sentence description of the paper's contribution

Write classifications to `classifications.json`.

## Implementation notes

- Use `requests` for API calls (stdlib-compatible, widely available)
- Sleep 1s between DBLP requests, 0.5s between OpenAlex requests
- OpenAlex abstract comes as an inverted index — reconstruct by sorting by position
- If a query returns 0 results, try relaxing it (drop venue prefix, broaden terms)
- Print progress as you go: `[12/48] Querying: NeurIPS 2024 domain generalization (47 new papers)`

## Example

User: `/paper-crawl out-of-distribution detection --venues NeurIPS,ICML,ICLR --years 2023-2025`

This will:
1. Generate 9 query combinations (3 venues x 3 years)
2. Query DBLP and OpenAlex for each (18 API calls)
3. Deduplicate results
4. Save to `papers.json`
5. Print summary
