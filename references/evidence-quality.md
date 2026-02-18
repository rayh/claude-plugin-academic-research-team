# Evidence Quality Reference

This reference material is available to all agents in this plugin. It encodes the shared understanding of how to assess evidence quality.

## Evidence Hierarchy

From strongest to weakest:

1. **Systematic reviews and meta-analyses** — Aggregate multiple studies, control for bias, quantify pooled effects. Gold standard when well-conducted.
2. **Randomised controlled trials (RCTs)** — Random assignment controls for confounders. Quality varies with blinding, sample size, and follow-up.
3. **Cohort studies** — Follow groups over time. Can establish temporal sequence but not causation.
4. **Case-control studies** — Compare cases with controls retrospectively. Susceptible to recall bias.
5. **Cross-sectional surveys** — Snapshot in time. Cannot establish causation or temporal sequence.
6. **Case reports and series** — Individual observations. Hypothesis-generating, not hypothesis-testing.
7. **Expert opinion** — Informed but subjective. Not evidence in itself.
8. **Mechanistic reasoning** — "It should work because..." — Plausible but often wrong in practice.

## Confidence Language Scale

| Evidence Strength | Language to Use |
|---|---|
| Strong consensus + high-quality evidence | "Evidence strongly indicates", "Well-established that" |
| Moderate evidence, mostly consistent | "Evidence suggests", "Current findings indicate" |
| Mixed or limited evidence | "Preliminary evidence suggests", "Some studies indicate" |
| Weak or conflicting evidence | "It has been proposed that", "Limited evidence exists for" |
| No direct evidence | "It is hypothesised that", "Theoretical considerations suggest" |

## Common Biases to Flag

- **Publication bias**: Positive/significant results are published more than null results
- **Funding bias**: Industry-funded studies more likely to report favourable outcomes
- **Citation bias**: Well-cited ≠ well-conducted; citation counts reflect influence, not quality
- **Survivorship bias**: Published literature over-represents successful approaches
- **Language bias**: English-language publication bias in international databases
- **Outcome reporting bias**: Selective reporting of outcomes within a study

## Citation Count Interpretation

Citation counts are useful but misleading without context:

| Paper Age | Citations | Rough Assessment |
|-----------|-----------|-----------------|
| < 1 year | > 50 | Exceptionally high interest |
| 1-3 years | > 100 | High impact |
| 3-5 years | > 500 | Very influential |
| 5-10 years | > 1000 | Seminal |
| > 10 years | > 5000 | Field-defining |

Caveats: Hot topics inflate counts. Self-citations inflate counts. Controversial papers get cited to be refuted. Citation counts in CS/ML are much higher than in other fields.

## Preprint vs Peer-Reviewed

- **Preprints** (arXiv, bioRxiv, medRxiv): Not peer-reviewed. May contain errors, be superseded, or be retracted. Valuable for timeliness but cite with caution.
- **Peer-reviewed**: Reviewed by experts but peer review is imperfect. Doesn't guarantee correctness — many peer-reviewed papers are later found to be flawed or irreproducible.
- **Always state which** when citing. "In a preprint, Author et al. report..." vs "In a peer-reviewed study, Author et al. found..."
