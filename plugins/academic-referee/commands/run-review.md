---
name: run-review
description: Run all referee reviews in parallel
arguments:
  - name: referees
    description: Comma-separated list of referee types (or 'all')
    required: false
---

# Run Parallel Referee Reviews

Execute reviews from all referee personas simultaneously using subagents.

## Your Task

1. **Identify what to review**: Find the paper, documentation, and code in the current directory

2. **Load referee personas**: Use the referee personas previously generated (or defaults if none exist)

3. **Launch parallel reviews**: Spawn each referee as a subagent using the Task tool:
   - Each referee reviews independently
   - Each produces a structured report
   - Reviews run in parallel for efficiency

4. **Collect and synthesize**: After all reviews complete:
   - Compile all feedback
   - Identify common themes
   - Highlight critical issues vs. minor suggestions
   - Note any conflicting recommendations

5. **Generate editorial summary**: Produce a summary like a journal editor would:
   - Overall recommendation (Accept / Minor Revisions / Major Revisions / Reject)
   - Key issues that must be addressed
   - Suggestions for improvement
   - Praise for strengths

## Default Referee Types (if not specified)

If no referee personas have been generated, use these defaults:
- **methodology**: Technical/methods expert
- **domain**: Application domain specialist
- **practitioner**: End-user perspective
- **reproducibility**: Code/data/replication focus
- **stylistic**: Writing style and presentation expert

## Referees to Run
{{ referees | default: "all" }}

## Output Format

```markdown
# Peer Review Summary

## Editorial Decision: [DECISION]

## Referee Reports

### Referee 1: [Title]
**Recommendation**: Accept / Minor / Major / Reject
**Summary**:
**Major Issues**:
**Minor Issues**:
**Strengths**:

### Referee 2: [Title]
...

## Synthesis

### Critical Issues (Must Address)
1.
2.

### Suggested Improvements
1.
2.

### Noted Strengths
1.
2.

## Next Steps
To address feedback: [specific guidance]
To re-run review after changes: `/run-review`
```
