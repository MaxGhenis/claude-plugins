---
name: review-cycle
description: Full iterative review cycle - find journal, generate referees, review, iterate until accept
arguments:
  - name: journal
    description: Target journal (optional - will help find one if not provided)
    required: false
---

# Full Academic Review Cycle

Complete workflow from journal selection through iterative review until acceptance.

## Workflow Steps

### Phase 1: Journal Selection
If no journal specified, run `/find-journal` to:
- Analyze the paper/software
- Search for suitable open access journals
- Recommend top options
- Get user confirmation on target journal

### Phase 2: Referee Generation
Run `/generate-referees` to:
- Research the target journal's review standards
- Create 3-4 domain-matched referee personas
- Always include a reproducibility reviewer
- Confirm referee panel with user

### Phase 3: Initial Review
Run `/run-review` to:
- Launch all referee reviews in parallel
- Collect structured feedback
- Synthesize into editorial decision
- Identify critical vs. minor issues

### Phase 4: Iteration Loop
Until unanimous "Accept" recommendation:

1. **Present feedback** to user with specific action items
2. **User addresses feedback** (code changes, writing revisions, etc.)
3. **Re-run reviews** with `/run-review`
4. **Track progress**: Note which issues are resolved, which remain
5. **Update decision**: Check if ready for acceptance

### Phase 5: Final Report
When all referees recommend Accept:
- Generate submission-ready checklist
- Confirm all reviewer concerns addressed
- Produce response-to-reviewers document template

## Target Journal (if provided)
{{ journal }}

## Your Task

Guide the user through this complete workflow. At each step:
- Explain what's happening
- Get user input when needed
- Track the state of the review process
- Celebrate progress!

Start by checking if there's a paper/software to review in the current directory.
