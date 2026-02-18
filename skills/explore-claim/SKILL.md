---
name: explore-claim
description: Open-ended exploration of an academic topic when the research question itself is unclear. Helps map a field, identify key debates, and formulate precise research questions.
disable-model-invocation: true
argument-hint: "[broad topic or vague question to explore]"
---

## Your task

Explore and map the academic landscape around: $ARGUMENTS

**This is exploratory research.** Unlike `/lit-review` (which answers a specific question) or `/confirm` (which evaluates a specific claim), this skill helps when you don't yet know what the right question is. The output is a map of the field, not an answer.

## Process

### Phase 1: Broad Reconnaissance

1. **Initial search**: Spawn a `literature-scout` to search broadly across Semantic Scholar and web search. Priority targets:
   - Survey papers and systematic reviews (these map the field efficiently)
   - Highly-cited foundational papers
   - Recent papers (last 2 years) that may signal new directions

2. **Identify structure**: From initial results, map:
   - Key sub-topics and how they relate
   - Major research groups and institutions
   - Dominant methodologies
   - Timeline of how the field evolved

### Phase 2: Identify Debates

3. **Find the fault lines**: Spawn a `critical-analyst` to identify:
   - What are the active debates in this field?
   - Where does the evidence conflict?
   - What assumptions are contested?
   - What methodological disagreements exist?

### Phase 3: Map and Recommend

4. **Produce a field map**:

   ```
   # Field Exploration: [Topic]

   ## Overview
   [2-3 paragraph summary of what this field is about, its history, and current state]

   ## Key Sub-Topics
   1. **[Sub-topic]**: [Brief description, key papers, current status]
   2. ...

   ## Active Debates
   1. **[Debate]**: [Side A] vs [Side B] — [current state of evidence]
   2. ...

   ## Seminal Papers
   [5-10 most influential papers with brief annotation of why they matter]

   ## Key Researchers and Groups
   - [Researcher/Group] at [Institution] — known for [contribution]

   ## Methodological Landscape
   - Dominant methods: [list]
   - Emerging methods: [list]
   - Methodological debates: [list]

   ## Suggested Research Questions
   Based on this exploration, here are precise, answerable research questions
   that could be investigated further with /lit-review or /confirm:

   1. [Question] — why it's interesting: [reason]
   2. ...

   ## Gaps and Opportunities
   - [Area that appears under-researched]
   - [Question that existing methods could answer but hasn't been addressed]

   ## References
   [Numbered list with DOI links]
   ```

## Important Reminders

- **Breadth over depth** — this is a mapping exercise, not a deep review
- **Name the unknown unknowns** — the most valuable output may be identifying what you don't know yet
- **Don't anchor on the first papers found** — actively seek diverse perspectives
- **Survey papers are gold** — a good survey does half the mapping work for you
