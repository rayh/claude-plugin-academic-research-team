Explore and map the academic landscape around: $ARGUMENTS

**This is exploratory research.** Unlike `/lit-review` (which answers a specific question) or `/confirm` (which evaluates a claim), this helps when you don't yet know what the right question is. The output is a map of the field, not an answer.

## Process

### Phase 1: Broad Reconnaissance

1. **Initial search**: Spawn a `literature-scout` to search broadly across Semantic Scholar and web search. Priority targets:
   - Survey papers and systematic reviews
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

### Phase 3: Map and Recommend

4. **Produce a field map**:

   ```
   # Field Exploration: [Topic]

   ## Overview
   [2-3 paragraph summary of what this field is about, its history, and current state]

   ## Key Sub-Topics
   1. **[Sub-topic]**: [Brief description, key papers, current status]

   ## Active Debates
   1. **[Debate]**: [Side A] vs [Side B] — [current state of evidence]

   ## Seminal Papers
   [5-10 most influential papers with brief annotation of why they matter]

   ## Key Researchers and Groups
   - [Researcher/Group] at [Institution] — known for [contribution]

   ## Suggested Research Questions
   Based on this exploration, here are precise questions for deeper investigation
   with /lit-review or /confirm:

   1. [Question] — why it's interesting: [reason]

   ## Gaps and Opportunities
   - [Area that appears under-researched]

   ## References
   [Numbered list with DOI links]
   ```
