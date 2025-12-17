# Anthropic Plugin Marketplace Submission

**Form:** https://docs.google.com/forms/d/e/1FAIpQLSdeFthxvjOXUjxg1i3KrOOkEPDJtn71XC-KjmQlxNP63xYydg/viewform

## academic-referee

| Field | Value |
|-------|-------|
| **Link to Plugin** | `https://github.com/MaxGhenis/claude-plugins/tree/main/plugins/academic-referee` |
| **Plugin Homepage** | `https://github.com/MaxGhenis/claude-plugins` |
| **Company/Organization URL** | `https://policyengine.org` |
| **Primary Contact Email** | `max@policyengine.org` |
| **Plugin Name** | `academic-referee` |

### Plugin Description (87 words)

Simulate academic peer review with journal-matched referee personas. Find suitable open access journals for your research, generate reviewer personas calibrated to each journal's standards, and run parallel reviews from multiple perspectives: methodology, domain expertise, practitioner usability, and reproducibility. Iterate through revisions until unanimous acceptance. The plugin launches specialized agents that provide structured feedback following real journal conventions, helping researchers strengthen their work before submission. Includes a reproducibility reviewer by default to ensure code, data, and documentation meet replication standards.

### Plugin Examples (3 use cases)

1. **Pre-submission review**: Before submitting a statistics paper to JASA, run `/review-cycle "Journal of the American Statistical Association"` to get feedback from methodology, domain, and reproducibility reviewers calibrated to JASA's standards.

2. **Journal selection**: Use `/find-journal "differentially private machine learning"` to discover suitable open access venues, then `/generate-referees` to understand what each journal's reviewers would prioritize.

3. **Iterative improvement**: After receiving "Major Revisions" feedback, address the issues and run `/run-review` again. Repeat until all referees recommend "Accept", ensuring your paper is submission-ready.
