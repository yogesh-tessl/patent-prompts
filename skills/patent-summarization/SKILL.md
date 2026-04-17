---
name: patent-summarization
description: "Generate a concise 2-3 paragraph summary of a patent from its claims, highlighting novel concepts and benefits. Use when the user wants to summarize a patent, get a quick overview of what a patent covers, explain a patent, or understand patent claims."
---

# Patent Summarization

Generate a concise 2-3 paragraph summary of a patent from its claims, highlighting novel concepts and benefits in bold.

## Inputs

Gather from the user or `$ARGUMENTS`:

| Placeholder | Required | Description |
|---|---|---|
| `{{PATENT_TITLE}}` | Yes | The title of the patent |
| `{{PATENT_ABSTRACT}}` | Yes | The abstract text from the patent |
| `{{PATENT_CLAIMS}}` | Yes | Full claims text (all claims, or at minimum the independent claims) |

## Workflow

1. Read the prompt at `${CLAUDE_SKILL_DIR}/../../prosecution/patent-summarization/prompt.md` and extract the section between `---` delimiters
2. Fill `{{PLACEHOLDER}}` values with user inputs
3. Execute the prompt to generate the summary
4. **Review**: Verify the summary highlights **novel concepts** in bold and stays within 2-3 paragraphs
5. Present the summary to the user

For best results, include all claims rather than just independent claims — dependent claims often contain the most specific novel features.
