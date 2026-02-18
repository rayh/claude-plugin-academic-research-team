# claude-plugin-academic-research-team

Rigorous academic research agents for Claude Code. Conducts literature reviews, evaluates claims against evidence, and explores academic fields — with proper citations, adversarial analysis, and honest confidence assessments.

## Philosophy

Academic research requires something most AI tools get wrong: **epistemic humility**. This plugin is designed around the principle that the strength of a claim depends on the strength of its evidence, and that evidence must be assessed honestly — including its limitations.

Every output includes:
- Proper citations with DOIs
- Explicit confidence levels with justification
- Balanced presentation of conflicting evidence
- Clear distinction between peer-reviewed and preprint sources
- Hedged language proportional to evidence strength

The adversarial analyst pair (critical + advocate) ensures no single perspective dominates. The research supervisor enforces academic integrity standards throughout.

## Agents

### Orchestration
| Agent | Role |
|-------|------|
| `research-supervisor` | Maintains scope, integrity, and academic standards. Coordinates specialists. |

### Search & Library
| Agent | Role |
|-------|------|
| `literature-scout` | Searches Semantic Scholar, arXiv, CrossRef, and web. Returns structured results. |
| `librarian` | Manages Zotero library, generates BibTeX, deduplicates references. |

### Analysis (Adversarial Pair)
| Agent | Role |
|-------|------|
| `critical-analyst` | Sceptical evaluator. Finds methodological flaws, contradictions, unstated assumptions. |
| `advocate-analyst` | Constructive evaluator. Steel-mans arguments, finds strongest supporting evidence. |

These two are designed to work in opposition — spawned together, they debate each other's findings, producing a balanced assessment that neither could achieve alone.

## Skills (Slash Commands)

| Command | What It Does |
|---------|-------------|
| `/lit-review [topic]` | Full structured literature review. Searches databases, spawns adversarial analysts, synthesises with citations. |
| `/confirm [claim]` | Evaluates evidence for and against a specific claim. Returns verdict with confidence level. |
| `/explore-claim [topic]` | Maps an unfamiliar field. Finds key debates, seminal papers, and suggests precise research questions. |

## Installation

### As Claude Code Plugin

```bash
/plugin install https://github.com/rayh/claude-plugin-academic-research-team
```

### Manual

```bash
git clone https://github.com/rayh/claude-plugin-academic-research-team.git
# Copy agents/ and skills/ to ~/.claude/ or your project's .claude/
```

### Optional: MCP Server Integration

For enhanced Zotero and Semantic Scholar access, install these MCP servers:

**Zotero** (library management):
```bash
uv tool install "git+https://github.com/54yyyu/zotero-mcp.git"
zotero-mcp setup
```

**Semantic Scholar** (native MCP tools):
```bash
npx -y @smithery/cli@latest install @JackKuo666/semanticscholar-mcp-server --client claude
```

The agents work without MCP servers (using direct API calls via Bash), but MCP integration provides a smoother experience.

### Environment Variables (Optional)

For Zotero API access without the MCP server:
```bash
export ZOTERO_API_KEY=your_key_here      # from zotero.org/settings/keys
export ZOTERO_USER_ID=your_user_id_here  # numeric ID
```

## Usage Examples

### Literature Review

```
/lit-review The effectiveness of spaced repetition for long-term knowledge retention in medical education
```

Produces a structured review with themes, consensus areas, debates, gaps, and full reference list.

### Claim Evaluation

```
/confirm Intermittent fasting improves cognitive function in healthy adults
```

Returns: verdict (Supported/Partially Supported/Contested/Unsupported/Insufficient Evidence), confidence level, evidence for and against, and quality assessment.

### Field Exploration

```
/explore-claim mechanistic interpretability in large language models
```

Maps the field: sub-topics, key debates, seminal papers, active researchers, and suggests precise questions for deeper investigation.

### Direct Agent Use

```
Use the critical-analyst to evaluate the methodology of the studies in this review
Use the literature-scout to find papers on CRISPR off-target effects published since 2023
Use the research-supervisor to coordinate a review of evidence on microplastics in drinking water
```

## Evidence Quality Standards

The plugin uses a shared evidence hierarchy (see `references/evidence-quality.md`):

1. Systematic reviews and meta-analyses
2. Randomised controlled trials
3. Cohort studies
4. Case-control studies
5. Cross-sectional surveys
6. Case reports
7. Expert opinion
8. Mechanistic reasoning

All agents use calibrated confidence language:

| Evidence Strength | Language |
|---|---|
| Strong consensus | "Evidence strongly indicates" |
| Moderate evidence | "Evidence suggests" |
| Mixed/limited | "Preliminary evidence suggests" |
| Weak/conflicting | "It has been proposed that" |
| No direct evidence | "It is hypothesised that" |

## Academic Data Sources

| Source | Used For | Auth Required |
|--------|----------|--------------|
| [Semantic Scholar](https://api.semanticscholar.org/) | Paper search, citation graphs, TLDRs | Free key recommended |
| [arXiv](http://export.arxiv.org/api) | Preprints, latest research | None |
| [CrossRef](https://api.crossref.org) | DOI resolution, BibTeX generation | None |
| [OpenAlex](https://api.openalex.org) | Broad metadata, institutions | Free key recommended |
| [Zotero](https://api.zotero.org) | Personal library management | API key required |

## Customisation

- **Adjust confidence thresholds**: Edit the evidence hierarchy in `references/evidence-quality.md`
- **Add domain expertise**: Create domain-specific reference files (e.g., `references/clinical-trials.md`) and reference them from agent prompts
- **Change models**: Upgrade analysts to `opus` for more nuanced evaluation on critical reviews
- **Add field-specific scouts**: Create specialised literature scouts for databases like PubMed, IEEE, or SSRN

## Prior Art & Acknowledgements

- [54yyyu/zotero-mcp](https://github.com/54yyyu/zotero-mcp) — Zotero MCP server
- [JackKuo666/semanticscholar-MCP-Server](https://github.com/JackKuo666/semanticscholar-MCP-Server) — Semantic Scholar MCP server
- [Semantic Scholar API](https://www.semanticscholar.org/product/api)
- [CrossRef API](https://www.crossref.org/documentation/retrieve-metadata/rest-api/)

## License

MIT
