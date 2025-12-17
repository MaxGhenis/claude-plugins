---
name: generate-referees
description: Generate referee personas matched to a target journal
arguments:
  - name: journal
    description: Target journal name
    required: true
  - name: count
    description: Number of referees (default 3-4)
    required: false
---

# Generate Journal-Matched Referee Personas

You are creating realistic referee personas that match what a journal editor would select for this paper.

## Your Task

1. **Understand the paper**: Read the paper/software documentation to identify:
   - Core methodology (what technical skills are needed to review?)
   - Application domain (what domain expertise is needed?)
   - Claims made (what needs verification?)
   - Software/reproducibility aspects

2. **Research the journal**: Look up the target journal to understand:
   - Editorial board composition
   - Types of reviewers they typically use
   - Review criteria and standards
   - What they emphasize (rigor, novelty, impact, reproducibility)

3. **Design referee personas**: Create 3-4 distinct reviewers plus a reproducibility reviewer:

   **Required perspectives**:
   - **Methodologist**: Expert in the core technical approach
   - **Domain Expert**: Specialist in the application area
   - **Practitioner/User**: Someone who would actually use this work
   - **Reproducibility Reviewer**: Focuses on code, data, replication (always included)

4. **For each referee, specify**:
   - Name/title (e.g., "Referee 1: Differential Privacy Theorist")
   - Background and expertise
   - What they'll focus on
   - Their likely concerns
   - Standards they'll apply

## Target Journal
{{ journal }}

## Output Format

Generate referee persona files that can be used as agents. For each referee, create a detailed prompt.

```markdown
## Referee Panel for [Journal Name]

### Referee 1: [Title]
**Expertise**:
**Focus areas**:
**Likely concerns**:
**Review standards**:

### Referee 2: [Title]
...

### Reproducibility Reviewer (Required)
**Focus**: Code quality, documentation, replication, data availability
**Standards**: Can results be reproduced? Is code well-documented?
```

After generating personas, ask if the user wants to proceed with `/run-review` to execute all reviews.
