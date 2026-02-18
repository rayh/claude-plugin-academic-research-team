---
name: confirm
description: Given a specific claim, find and evaluate the academic evidence for and against it. Returns a balanced assessment with confidence level and proper citations.
disable-model-invocation: true
argument-hint: "[specific claim to evaluate]"
---

## Your task

Evaluate the evidence for and against this claim: $ARGUMENTS

**This is a rigorous evidence assessment, not a fact-check.** The output must present both sides fairly, assess evidence quality, and give an honest confidence level. The goal is to help someone understand what the science actually says — including its uncertainties.

## Process

### Phase 1: Search

1. **Decompose the claim**: Break it into testable sub-claims if it's compound. Identify the key empirical assertions.

2. **Search for evidence**: Create an agent team with 2 `literature-scout` teammates:
   - Scout 1: Search for evidence **supporting** the claim (use affirmative search terms)
   - Scout 2: Search for evidence **against** the claim (use contradictory/alternative terms)

   Both scouts must search Semantic Scholar and at least one other source.

### Phase 2: Adversarial Analysis

3. **Spawn analysts**:
   - `advocate-analyst`: Build the strongest evidence-based case FOR the claim
   - `critical-analyst`: Build the strongest evidence-based case AGAINST the claim

   Both must cite specific papers. Neither may ignore inconvenient evidence.

4. **Cross-examination**: Have each analyst message the other with their strongest challenge. Each must respond to the other's best point.

### Phase 3: Verdict

5. **Synthesise** into a balanced assessment:

   ```
   # Evidence Assessment: [Claim]

   ## Claim Evaluated
   [Precisely stated, with any necessary disambiguation]

   ## Verdict: [Supported / Partially Supported / Contested / Unsupported / Insufficient Evidence]

   ## Confidence: [High / Medium / Low]
   [One sentence justifying the confidence level]

   ## Evidence For
   [Strongest evidence supporting the claim, with citations and quality assessment]

   ## Evidence Against
   [Strongest evidence contradicting the claim, with citations and quality assessment]

   ## Nuances and Caveats
   - [Important context that affects interpretation]
   - [Boundary conditions: where the claim holds vs. doesn't]
   - [Common misinterpretations of the evidence]

   ## Evidence Quality Summary
   | Direction | Studies | Best Evidence Level | Consistency |
   |-----------|---------|-------------------|-------------|
   | For       | N       | [RCT/meta-analysis/etc] | [High/Mixed/Low] |
   | Against   | N       | [RCT/meta-analysis/etc] | [High/Mixed/Low] |

   ## What Would Change This Assessment
   - Evidence that would increase confidence: [specific]
   - Evidence that would decrease confidence: [specific]

   ## References
   [Numbered list with DOI links]
   ```

## Verdict Definitions

- **Supported**: Strong, consistent evidence from high-quality studies. Scientific consensus aligns.
- **Partially Supported**: Evidence supports the claim in some contexts but not others, or with important caveats.
- **Contested**: Substantial evidence exists on both sides. Active scientific debate.
- **Unsupported**: Available evidence does not support the claim, or contradicts it.
- **Insufficient Evidence**: Not enough research exists to evaluate. Absence of evidence ≠ evidence of absence.

## Important Reminders

- A claim can be **popular and wrong**, or **unpopular and right**. Follow the evidence, not the consensus count.
- **Effect sizes matter more than p-values.** A statistically significant but tiny effect may not support a strong claim.
- **Distinguish "not proven" from "proven not."** These are very different statements.
- **Publication bias is real.** If you only find supporting evidence, note that negative results may be unpublished.
