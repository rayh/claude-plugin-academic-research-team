---
name: ask
description: Answer a science question using academic sources. Optionally provide a DOI, arXiv ID, or paper title to ground the answer in a specific paper.
disable-model-invocation: true
argument-hint: "[question] or [question] --paper [DOI/arXiv ID/title]"
---

## Your task

Answer this science question using academic evidence: $ARGUMENTS

**This is a quick, grounded answer — not a full literature review.** Think of it as asking a knowledgeable colleague who always cites their sources and says "I'm not sure" when they're not sure.

## Process

### Step 1: Parse the question

Check if the user provided a specific paper reference:
- `--paper DOI:10.xxx/yyy` or `--paper 2301.12345` or `--paper "Some Paper Title"`
- If a paper is specified, retrieve it first and ground the answer primarily in that paper
- If no paper is specified, search for the most relevant evidence

### Step 2: Find evidence

**If a specific paper was provided:**

```bash
# By DOI
curl -s 'https://api.semanticscholar.org/graph/v1/paper/DOI:PAPER_DOI?fields=title,abstract,year,citationCount,authors,venue,openAccessPdf,tldr,references' | python3 -m json.tool

# By arXiv ID
curl -s 'https://api.semanticscholar.org/graph/v1/paper/ArXiv:ARXIV_ID?fields=title,abstract,year,citationCount,authors,venue,openAccessPdf,tldr,references' | python3 -m json.tool

# By title search
curl -s 'https://api.semanticscholar.org/graph/v1/paper/search?query=TITLE_KEYWORDS&limit=3&fields=title,abstract,year,citationCount,authors,venue,tldr' | python3 -m json.tool
```

Read the abstract and TLDR. If an open access PDF is available, note the URL for the user.

**If no paper was specified:**

Search Semantic Scholar for the 3-5 most relevant papers:

```bash
curl -s 'https://api.semanticscholar.org/graph/v1/paper/search?query=SEARCH_TERMS&limit=5&fields=title,abstract,year,citationCount,authors,venue,tldr,externalIds' | python3 -m json.tool
```

Prioritise: meta-analyses > RCTs > reviews > primary studies. Prefer recent, well-cited work.

### Step 3: Answer the question

Produce a clear, direct answer:

```
## [Restated question]

**Short answer**: [1-2 sentence direct answer]

**What the evidence says**:
[2-4 paragraphs explaining the answer with inline citations [1]. Include
relevant nuance — boundary conditions, caveats, and confidence level.
Use calibrated language: "evidence strongly suggests" for well-established
findings, "preliminary evidence indicates" for emerging work.]

**Confidence**: [High/Medium/Low]
[One sentence: why this confidence level? e.g., "High — supported by
multiple meta-analyses with consistent findings" or "Low — based on
a single small-sample study"]

**Important caveats**:
- [Anything that qualifies the answer — context where it might not hold,
  ongoing debates, methodological concerns]

**References**:
1. Author et al. (Year). "Title." *Venue*.
   DOI: [10.xxx/yyy](https://doi.org/10.xxx/yyy)
```

### If grounded in a specific paper:

Add a section about the paper itself:

```
**About this paper**:
- **Title**: [full title]
- **Authors**: [author list]
- **Published**: [venue, year]
- **Citations**: [count] (as of search date)
- **Key finding**: [TLDR or one-sentence summary]
- **Methodology**: [brief description]
- **Limitations noted by authors**: [if available from abstract]
```

## Guidelines

- **Answer the question first**, then provide evidence. Don't make the user wade through a literature review to find the answer.
- **Be direct.** "Yes, evidence supports this" or "No, current evidence does not support this" or "It's complicated — here's why."
- **Cite everything.** Even a quick answer needs references.
- **Say when you're uncertain.** "The evidence on this is limited" is a valid and useful answer.
- **Don't overstate a single paper.** If the answer is grounded in one paper, note that this is one study and may not represent consensus.
- **Note recency.** If the most relevant work is from 2015, say so — the field may have moved on.
- **Distinguish established science from frontier research.** "Water boils at 100C at sea level" needs different treatment than "RLHF may cause reward hacking."
