# Changelog

## March 2026

### Open-Source Launch (March 18)

ArcPrime open-sourced **patent-prompts** — a collection of 15 professional patent workflow prompts built by Jon Liu (former patent counsel at Meta and Fish & Richardson). These are production-tested prompts covering the full patent lifecycle, from pre-filing through prosecution to portfolio management.

#### Pre-Filing Prompts

- **Claims Drafting** — Drafts patent claims from an invention disclosure at the broadest defensible scope. Builds independent claims focused on *how* the invention works (not what it achieves), then layers dependent claims as fallback positions. Includes adversarial stress-testing against 102/103 rejections, antecedent basis validation, and a scope verification framework (competitor avoidance test, embodiment vs. invention test, element movement analysis).

- **Disclosure Questions** — Generates 10 strategic questions to enrich an invention disclosure before drafting. Uses a five-category framework (Technical Clarification, Inventive Insight Extraction, Claim Strategy, Alternative Embodiments, Commercial Context) with priority scoring (1-10) to maximize limited inventor time.

- **Draft Review (Combined 101 + 112)** — Reviews a patent draft for both Section 101 eligibility risks and Section 112 issues before filing. Outputs a prioritized issue list with paste-ready remedies. For 101: evaluates technical improvement disclosures against Enfish, McRO, DDR Holdings, and Visual Memory precedents. For 112: runs written description, enablement (Wands Factors), indefiniteness, antecedent basis, and means-plus-function (3-prong test) checks. Produces a severity matrix and filing-readiness verdict.

- **Draft Review (101 Only)** — Focused 101 eligibility review using an Evidence Lexicon methodology — extracts key technical terms, maps co-occurrences, and builds verb-object pairs from the specification to generate paste-ready language that strengthens the 101 position. Includes a case law alignment table rating strength against four key precedents.

- **Draft Review (112 Only)** — Focused 112 compliance review covering five issue types: written description (112a), enablement via Wands Factors (112a), indefiniteness (112b), antecedent basis, and means-plus-function (112f). Generates complete verbatim claim replacements — no abbreviations or ellipses — with all vocabulary sourced from the specification's Evidence Lexicon.

- **Prior Art Analysis** — Analyzes independent claims against prior art using the full 102 anticipation and 103 obviousness frameworks. Applies Graham v. John Deere factors and all six KSR obviousness rationales. For each claim deemed non-obvious, provides adversarial stress-testing: states the strongest examiner argument for obviousness and explains why it fails. Outputs an element-by-element comparison table and a claim vulnerability matrix with risk labels.

- **Detectability Assessment** — Evaluates how easily an invention's implementation can be detected in potentially infringing products. Maps each claim element to where it manifests (client-side, server-side, network, manufacturing, output), specifies required detection methods with cost/time estimates, identifies barriers to detection, and includes an adversarial assessment of the strongest undetectability counterargument. Helps decide whether to patent and how to structure claims for maximum enforceability.

#### Prosecution Prompts

- **Patent Summarization** — Generates a concise 2-3 paragraph summary of a patent from its claims, highlighting novel concepts and benefits in bold. Prioritizes dependent claims as sources for specific technical details.

- **Concept Extraction** — Extracts 3-8 core patent concepts by identifying the inventive technical approaches that make the innovation non-obvious. Distinguishes between product concepts (user value) and patent concepts (inventive technical approach). Each concept includes a description, supporting claim numbers, and strategic context for prosecution, licensing, and portfolio planning.

#### Portfolio Prompts

- **Continuation — Targeted** — Drafts continuation claims designed to cover a specific competitor product, using only vocabulary found verbatim in the patent specification. Includes web search integration for competitor product details, divided infringement avoidance analysis, and a claim-evidence mapping table tracing every element back to the detailed description with support confidence ratings.

- **Continuation — Broadened** — Identifies where examiners forced narrowing during prosecution and generates broader independent claims for continuation applications. Compares original vs. amended claims to find broadening opportunities, builds an Evidence Lexicon with co-occurrence tracking, and assesses 112 rejection risk for each broadened claim.

- **Continuation — Unclaimed Subject Matter** — Mines the specification to find disclosed subject matter that was never claimed. Performs coverage gap analysis (fully unclaimed, partially unclaimed, unclaimed combinations), ranks discoveries by commercial value (breadth potential, industry relevance, enforceability, specification support depth), and generates continuation claims in priority filing order.

- **Claim Chart** — Maps patent claim elements to features of an accused product across three infringement theories: literal, induced, and doctrine of equivalents. Enforces six anti-speculation rules (no fabrication, mechanism vs. outcome distinction, no speculative language, no self-contradiction, no claim paraphrasing as evidence, logical consistency). Outputs an element-by-element mapping table with a coverage scorecard and strongest defense argument per element.

- **Categorization** — Categorizes patents into a user-provided technology taxonomy with a primary category, subcategory, confidence rating (High/Medium/Low), and alternative suggestion when confidence is uncertain. Focuses on core technical innovation rather than application domain.

- **Pruning Analysis** — Evaluates whether a patent case should be maintained or pruned relative to other cases in the same family. Uses a five-tier determination system (BROADEST, COMPLEMENTARY, NARROW, SUNSET, REVIEW) based on claim scope comparison, patent life remaining, and jurisdictional overlap.

#### Examples and Documentation

- **Sample Patent** — Adaptive Traffic Signal Control System Using Real-Time Pedestrian Detection. Includes 3 independent claims (method, system, computer-readable medium) with 9 dependent claims covering multi-stage pedestrian detection, predictive queue models, and adaptive signal timing.

- **Sample Disclosure** — Context-Aware Emergency Vehicle Preemption System for Connected Intersections. Covers V2I communication, multi-strategy preemption (early green termination, phase insertion, pedestrian flush, queue discharge), and graduated recovery sequencing.

- **15 Pre-Filled Examples** — Every prompt has a "try it now" example using the sample patent or disclosure data, so users can see real output immediately.

---

### Installable AI Agent Skills (March 22)

All 15 prompts became installable slash commands across multiple AI coding agents.

- **Claude Code Plugin** — Added `.claude-plugin/plugin.json` manifest. Install with `/plugin install patent-prompts@arcprime-ip/patent-prompts`, then run any prompt as `/patent-prompts:<skill-name>` (e.g., `/patent-prompts:claims-drafting`, `/patent-prompts:claim-chart`).

- **15 SKILL.md Files** — Universal agent skill format in `skills/` directory. Each skill wraps the corresponding prompt file, specifies required user inputs, handles placeholder substitution, and guides output presentation.

- **OpenAI Codex CLI Support** — Added `AGENTS.md` with instructions for Codex CLI integration.

- **Multi-Platform Compatibility** — Skills work with Claude Code, OpenAI Codex CLI, Cursor, and Gemini CLI.

- **Web Search Integration** — Prompts that benefit from live data (prior-art-analysis, claim-chart, continuation-targeted) support web search when available in the agent environment.
