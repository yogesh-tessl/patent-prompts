---
name: draft-review
description: "Review a patent application draft for Section 101 eligibility risks and Section 112 issues before filing, providing a prioritized list of problems with paste-ready remedies. Use when the user wants to review a patent draft, check patentability, or do a pre-filing review."
---

# Patent Draft Review (101 + 112 Combined)

Review a patent draft (specification and claims) for both Section 101 eligibility risks and Section 112 issues before filing, providing a prioritized list of problems with paste-ready remedies.

## Inputs

Gather from the user or `$ARGUMENTS`:

| Placeholder | Required | Description |
|---|---|---|
| `{{PATENT_DRAFT}}` | Yes | Patent specification and claims |

If the user provides a file path or pasted content as `$ARGUMENTS`, use that as the draft.

## Workflow

1. Read the prompt at `${CLAUDE_SKILL_DIR}/../../pre-filing/draft-review/prompt.md` and extract the section between `---` delimiters
2. Fill `{{PLACEHOLDER}}` values with user inputs
3. Execute the prompt to perform the review
4. **Review**: Confirm analysis covers 101 eligibility (Alice/Mayo framework, Enfish technical improvement test) and 112 requirements (written description, enablement, definiteness)
5. Present the prioritized findings with remedies to the user

## Variants

For focused reviews, also available:
- `/patent-prompts:draft-review-101` — Section 101 only
- `/patent-prompts:draft-review-112` — Section 112 only

## Example Output Format

```
## Priority 1 (High) — 101 Risk: Abstract Idea
Issue: Claim 1 recites [abstract concept] without technical improvement
Remedy: Add "wherein [specific technical improvement]..." to claim 1
```
