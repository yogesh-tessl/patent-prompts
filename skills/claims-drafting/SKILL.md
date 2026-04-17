---
name: claims-drafting
description: "Draft independent and dependent patent claims from an invention disclosure, covering method, system, and apparatus claim types at the broadest defensible scope. Use when the user wants to draft claims, write claims from a disclosure, generate patent claims for a new invention, or create a claim set."
---

# Patent Claims Drafting

Draft patent claims from an invention disclosure — one independent claim at the broadest defensible scope plus dependent claims with specific implementation details as fallback positions.

## Inputs

Gather from the user or `$ARGUMENTS`:

| Placeholder | Required | Description |
|---|---|---|
| `{{INVENTION_TITLE}}` | Yes | Title of the invention |
| `{{INVENTION_DESCRIPTION}}` | Yes | What it does, how it works, what problem it solves |
| `{{KEY_DIFFERENCE}}` | Yes | What makes it different from existing solutions |
| `{{SUPPORTING_DOCUMENTS}}` | No | Additional technical documents |
| `{{REFERENCE_CLAIMS}}` | No | Claims from a similar patent for style guidance |

If the user provides a file path or pasted content as `$ARGUMENTS`, use that as the invention disclosure and extract the needed fields from it.

## Workflow

1. Read the prompt at `${CLAUDE_SKILL_DIR}/../../pre-filing/claims-drafting/prompt.md` and extract the section between `---` delimiters
2. Fill `{{PLACEHOLDER}}` values with user inputs
3. Execute the prompt to draft claims
4. **Review**: Verify independent claims use broadest defensible scope, dependent claims add meaningful narrowing, and all claim elements trace to the disclosure
5. Present the drafted claims to the user

## Example Output Format

```
Claim 1 (Independent — Method):
A method for [broadest scope], comprising:
  (a) [first step]...
  (b) [second step]...

Claim 2 (Dependent on Claim 1):
The method of claim 1, wherein [specific implementation detail].
```
