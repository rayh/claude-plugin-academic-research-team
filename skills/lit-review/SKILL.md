---
name: lit-review
description: Conduct a structured literature review on a topic using multiple specialist agents searching academic databases, then critically analyse and synthesise findings with proper citations
disable-model-invocation: true
argument-hint: "[research topic or question]"
---

## Your task

Conduct a structured literature review on: $ARGUMENTS

**This is an academic literature review.** The output must be balanced, properly cited, and honest about the strength of evidence. Every factual claim must be traceable to a source.

## Process

### Phase 1: Scope and Search

1. **Frame the question**: Restate the research topic as a precise research question. Identify key terms, synonyms, and related concepts. Note any ambiguity and state your interpretation.

2. **Search broadly**: Create an agent team and spawn 2-3 `literature-scout` teammates, each searching with different query strategies:
   - Scout 1: Core keywords via Semantic Scholar (relevance-ranked)
   - Scout 2: Recent work via arXiv + broader web search
   - Scout 3: Citation graph traversal — find seminal papers, then trace who cited them

   Each scout should return structured results with title, authors, year, venue, citation count, abstract excerpt, and relevance assessment.

3. **Deduplicate and rank**: Collect all results, remove duplicates (match on DOI), rank by relevance and quality signals (citation count normalised by age, venue quality, methodology).

### Phase 2: Critical Analysis

4. **Spawn analysts**: Create two analyst teammates:
   - `critical-analyst`: Evaluate the body of evidence sceptically. Find methodological weaknesses, contradictions, gaps, and unstated assumptions.
   - `advocate-analyst`: Present the strongest case for the emerging consensus. Find convergent evidence, theoretical support, and address known criticisms.

   Both analysts review the same set of papers found in Phase 1.

5. **Debate**: Have the analysts message each other to challenge each other's assessments. The critical analyst should attack the advocate's strongest claims. The advocate should defend against the critic's strongest objections.

### Phase 3: Synthesis

6. **Synthesise findings** into a structured literature review:

   ```
   # Literature Review: [Topic]

   ## Research Question
   [Precisely stated]

   ## Methodology
   - Sources searched: [list databases and date ranges]
   - Search queries: [list key queries used]
   - Papers identified: N total, M included after filtering
   - Date range: [earliest] to [latest]

   ## Current State of Knowledge
   [Organised by theme or chronology. Every claim cited.]

   ## Areas of Consensus
   [What the evidence broadly agrees on. Note strength of consensus.]

   ## Areas of Debate
   [Where evidence is contradictory or inconclusive. Present both sides fairly.]

   ## Methodological Considerations
   [Common limitations across studies. What kinds of evidence are missing?]

   ## Gaps in the Literature
   [What questions remain unanswered? What research is needed?]

   ## Confidence Assessment
   [How strong is the overall evidence base? What would change this assessment?]

   ## References
   [Numbered list with DOI links. Every citation in the text must appear here.]
   ```

7. **Optionally save to Zotero**: If the `librarian` agent is available and Zotero is configured, save the found papers to a new Zotero collection named after the research topic.

## Important Reminders

- **Tentative language**: Use "evidence suggests", "findings indicate", not "studies prove"
- **Publication bias**: Note that positive results are over-represented in the literature
- **Recency**: Flag if the field is fast-moving and findings may already be superseded
- **Preprint caution**: Clearly distinguish peer-reviewed from preprint sources
- **Honest gaps**: It's better to say "insufficient evidence" than to overstate weak findings
