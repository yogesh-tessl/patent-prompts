---
name: prior-art-analysis
description: "Analyze patent claims against prior art using 35 U.S.C. 102 (anticipation) and 103 (obviousness) framework, including Graham v. John Deere factors and KSR rationales. Use when the user wants prior art analysis, novelty assessment, obviousness evaluation, or patentability review."
---

# Prior Art Analysis

Analyze independent patent claims against prior art using the full 35 U.S.C. 102 (anticipation) and 103 (obviousness) framework, including Graham v. John Deere factors and KSR rationales.

This skill benefits from **web search** to find relevant prior art references.

## Inputs

Gather from the user or `$ARGUMENTS`:

| Placeholder | Required | Description |
|---|---|---|
| `{{INDEPENDENT_CLAIMS}}` | Yes | Independent claims to analyze |
| `{{WEB_SEARCH_RESULTS}}` | No | Known prior art or web search results |

## Workflow

1. Read the prompt at `${CLAUDE_SKILL_DIR}/../../pre-filing/prior-art-analysis/prompt.md` and extract the section between `---` delimiters
2. Fill `{{PLACEHOLDER}}` values with user inputs
3. If web search is available, search for relevant prior art references before executing
4. Execute the prompt to perform the analysis
5. **Review**: Confirm 102 analysis uses single-reference rule and 103 analysis addresses all Graham factors
6. Present the analysis to the user

## Example Output Format

```
## 102 Analysis (Anticipation)
Claim 1 vs. [Reference]: Element (a) disclosed at [col:line] — Element (b) NOT disclosed → Claim survives 102

## 103 Analysis (Obviousness)
Graham Factor 1 — Scope of prior art: [assessment]
Motivation to combine: [rationale or absence]
```
