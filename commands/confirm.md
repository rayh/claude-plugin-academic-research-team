Evaluate the evidence for and against this claim: $ARGUMENTS

**This is a rigorous evidence assessment, not a fact-check.** The output must present both sides fairly, assess evidence quality, and give an honest confidence level.

## Process

### Phase 1: Search

1. **Decompose the claim**: Break it into testable sub-claims if it's compound. Identify the key empirical assertions.

2. **Search for evidence**: Create an agent team with 2 `literature-scout` teammates:
   - Scout 1: Search for evidence **supporting** the claim
   - Scout 2: Search for evidence **against** the claim

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

- **Supported**: Strong, consistent evidence from high-quality studies.
- **Partially Supported**: Evidence supports in some contexts but not others.
- **Contested**: Substantial evidence on both sides. Active debate.
- **Unsupported**: Available evidence does not support or contradicts it.
- **Insufficient Evidence**: Not enough research to evaluate. Absence of evidence ≠ evidence of absence.
