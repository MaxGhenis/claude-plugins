---
name: find-journal
description: Find suitable open access journals for your paper/software
arguments:
  - name: topic
    description: Brief description of your paper topic
    required: false
---

# Find Suitable Open Access Journals

You are helping a researcher find the best open access journal for their work.

## Your Task

1. **Understand the work**: Read any paper, README, or documentation in the current directory to understand:
   - Research domain (economics, ML, statistics, etc.)
   - Methodology (empirical, theoretical, software)
   - Target audience (practitioners, academics, policymakers)

2. **Search for suitable journals**: Use web search to find open access journals that:
   - Publish work in this domain
   - Accept this type of contribution (research article, software paper, methods paper)
   - Have reasonable review timelines
   - Are well-regarded in the field

3. **Evaluate fit**: For each candidate journal, assess:
   - Scope alignment (does the journal publish this type of work?)
   - Impact/reputation (impact factor, community standing)
   - Open access model (fully OA, hybrid, APC costs)
   - Review process (single-blind, double-blind, open review)
   - Typical turnaround time

4. **Recommend top 3-5 journals** with:
   - Journal name and URL
   - Why it's a good fit
   - Submission requirements
   - Estimated APC (if any)
   - Notable papers in similar areas

## User's Topic (if provided)
{{ topic }}

## Output Format

```markdown
## Recommended Journals for [Paper Title/Topic]

### 1. [Journal Name] (Recommended)
- **URL**:
- **Publisher**:
- **Fit Score**: X/10
- **Why it fits**:
- **APC**:
- **Review type**:
- **Similar published work**:

### 2. [Journal Name]
...
```

After presenting options, ask the user which journal they'd like to target so you can generate appropriate referee personas.
