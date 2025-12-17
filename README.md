# Max Ghenis Claude Plugins

A collection of Claude Code plugins for research, policy analysis, and development.

## Installation

```bash
/plugin marketplace add MaxGhenis/claude-plugins
```

Then install individual plugins:

```bash
/plugin install academic-referee@maxghenis-plugins
```

## Available Plugins

### academic-referee

**Multi-perspective academic paper review with journal-matched referee personas.**

Simulates the peer review process to help improve your research before submission.

#### Workflow

1. **Find a journal**: `/find-journal [topic]`
   - Analyzes your paper/software
   - Searches for suitable open access journals
   - Recommends top 3-5 venues with fit assessment

2. **Generate referees**: `/generate-referees <journal>`
   - Researches the target journal's standards
   - Creates 3-4 domain-matched referee personas
   - Always includes a reproducibility reviewer

3. **Run reviews**: `/run-review [referees]`
   - Launches all referee reviews in parallel
   - Each referee produces structured feedback
   - Synthesizes into editorial decision

4. **Full cycle**: `/review-cycle [journal]`
   - Complete workflow from journal selection to acceptance
   - Iterates until all referees recommend Accept

#### Default Referee Personas

| Referee | Focus |
|---------|-------|
| **Methodology** | Mathematical rigor, statistical validity, algorithmic correctness |
| **Domain Expert** | Application relevance, related work, field context |
| **Practitioner** | Usability, documentation, practical value |
| **Reproducibility** | Code quality, tests, documentation, replication |

#### Example Usage

```bash
# Start the full review cycle
/review-cycle

# Or step by step:
/find-journal "differentially private econometrics"
/generate-referees "Journal of Privacy and Confidentiality"
/run-review
```

## Creating New Plugins

Add new plugins to `plugins/` directory:

```
plugins/
└── my-new-plugin/
    ├── plugin.json
    ├── commands/
    ├── agents/
    └── skills/
```

Then add to `.claude-plugin/marketplace.json`.

## License

MIT

## Author

Max Ghenis (max@policyengine.org)
