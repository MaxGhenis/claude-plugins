---
name: paper-review
description: Automatically offer academic review workflow when user has a paper or research software ready for submission
triggers:
  - "review my paper"
  - "ready for submission"
  - "peer review"
  - "find a journal"
  - "submit to journal"
  - "referee feedback"
  - "manuscript review"
---

# Academic Paper Review Skill

This skill activates when you detect the user has research work ready for review or journal submission.

## When to Activate

Offer this workflow when:
- User mentions submitting a paper
- User asks about journal selection
- User wants feedback on research
- User has a paper/notebook in the directory
- User asks for peer review

## What to Offer

When activated, briefly explain the workflow:

```
I can help you through an academic review cycle:

1. **Find a journal**: Search for suitable open access journals for your work
2. **Generate referees**: Create reviewer personas matched to the journal
3. **Run reviews**: Get parallel feedback from multiple perspectives
4. **Iterate**: Address feedback and re-review until ready

Would you like to start with `/find-journal` to identify target venues, or `/review-cycle` for the full workflow?
```

## Available Commands

- `/find-journal [topic]` - Find suitable open access journals
- `/generate-referees <journal>` - Create journal-matched referee personas
- `/run-review [referees]` - Execute reviews in parallel
- `/review-cycle [journal]` - Full iterative workflow

## Default Reviewers

If no custom referees are generated, these defaults are used:
- **Methodology Reviewer**: Technical/mathematical rigor
- **Domain Reviewer**: Application expertise and context
- **Practitioner Reviewer**: End-user perspective
- **Reproducibility Reviewer**: Always included - code, data, replication
