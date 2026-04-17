---
name: concept-extraction
description: "Extract core inventive technical concepts from patent claims for prior art analysis, claim drafting, continuation planning, and IP strategy. Use when the user wants to identify inventive concepts, analyze patent claims, map patent-to-product features, or understand technical approaches in a patent."
---

# Patent Concept Extraction

Extract the core patent concepts from a set of patent claims — identifying the inventive technical approaches that make the innovation non-obvious, not just restating claim language or listing product features.

## Inputs

Gather from the user or `$ARGUMENTS`:

| Placeholder | Required | Description |
|---|---|---|
| `{{PATENT_TITLE}}` | Yes | Title of the patent |
| `{{PATENT_CLAIMS}}` | Yes | Patent claims to analyze |

## Workflow

1. Read the prompt at `${CLAUDE_SKILL_DIR}/../../prosecution/concept-extraction/prompt.md` and extract the section between `---` delimiters
2. Fill `{{PLACEHOLDER}}` values with user inputs
3. Execute the prompt to extract concepts
4. **Review**: Verify each extracted concept maps to specific claim language and represents an inventive step, not just a product feature
5. Present the extracted concepts to the user

## Example Output Format

```
Concept 1: [Technical approach name]
  Claims: 1, 3, 7
  Inventive step: [What makes this non-obvious]
  Prior art relevance: [How this differentiates from known art]
```
