---
name: paper-writing
description: Academic paper writing with MyST markdown — formatting, common pitfalls, and patterns from iterative peer review
triggers:
  - "write paper"
  - "write a paper"
  - "academic writing"
  - "myst formatting"
  - "myst paper"
  - "format paper"
  - "paper formatting"
  - "writing style"
  - "scholarly writing"
  - "journal paper"
  - "latex paper"
---

# Academic paper writing with MyST

Hard-won patterns from iterative peer review cycles. Use this skill when writing or editing academic papers in MyST markdown format.

## MyST formatting

### Dashes do not auto-convert

MyST does NOT convert ASCII dashes to Unicode. Use actual Unicode characters:

- **Em-dash** (`—`, U+2014): Use for parenthetical breaks. Type `—` directly, never `---`.
  - WRONG: `the double distortion mechanism---which we identify`
  - RIGHT: `the double distortion mechanism—which we identify`

- **En-dash** (`–`, U+2013): Use for number ranges. Type `–` directly, never `--`.
  - WRONG: `elasticities of 0.1--0.3`
  - RIGHT: `elasticities of 0.1–0.3`

- **Hyphen** (`-`): Only for compound words (`income-based`, `well-known`).

### LaTeX backslash commands render literally

MyST is not LaTeX. Backslash commands outside of math mode are not interpreted — they render as literal text. Common offenders:

| LaTeX | Intended effect | MyST renders as | Fix |
|---|---|---|---|
| `vs.\ 0.343` | Normal space after abbreviation | `vs.\ 0.343` | `vs. 0.343` |
| `\,` | Thin space | `\,` | Just use a space |
| `\;` | Medium space | `\;` | Just use a space |
| `\!` | Negative space | `\!` | Remove it |
| `~` | Non-breaking space (LaTeX) | `~` (literal tilde) | Use Unicode NBSP (U+00A0) |
| `\textbf{x}` | Bold | `\textbf{x}` | `**x**` |
| `\emph{x}` | Italic | `\emph{x}` | `*x*` |

Inside `$...$` math mode, LaTeX commands work normally. The issue is only in prose text.

### Currency and dollar signs

Escape dollar signs for currency; unescaped `$` triggers math mode:
```
WRONG: a $200 fine
RIGHT: a \$200 fine
```

### Citations

Use `{cite}` syntax, never hardcoded text:
```
WRONG: Chetty (2012) shows...
RIGHT: {cite}`chetty2012` shows...
```

Use `{cite:p}` for parenthetical—never wrap `{cite}` in parens:
```
WRONG: ({cite}`chetty2012`)     → renders as "(Chetty (2012))"
RIGHT: {cite:p}`chetty2012`     → renders as "(Chetty, 2012)"
```

### Cross-references

Label equations and reference them:
```
$$U_i = \log(1 + c_i) + \alpha \log(1 + s_i)$$ (eq:utility)

From {eq}`eq:utility`, the marginal utility...
```

### Tables

`list-table` requires a list of lists (common build error):
```
\`\`\`{list-table} Caption text
:header-rows: 1
:name: tab:my-table

* - Column A
  - Column B
* - value 1
  - value 2
\`\`\`
```

Reference with `{numref}`:
```
{numref}`tab:my-table` summarizes the parameters.
```

### Building and previewing

```bash
cd paper && bunx mystmd start    # Dev server (hot reload)
bunx mystmd build --pdf           # Static PDF
```

`myst.yml` config: the `build` key is not a top-level config option (triggers a warning). Put execution settings elsewhere.

## Writing patterns from peer review

### Every number must have a source

Never hardcode numerical results in prose. Pull from your results file or derivation:
- `results.json` is the single source of truth for simulation outputs
- If a number appears in the paper, it must match the code output exactly
- When results change (new calibration, more draws), grep for stale values

### Replace vague qualifiers with specific numbers

Referees flag vague adjectives immediately. Always quantify:

| Vague (rejected) | Specific (accepted) |
|---|---|
| "modest additional tax" | "0.2–2 percentage points" |
| "substantially better deterrence" | "more uniform deterrence" or give the number |
| "the effect is small" | "the effect is an order of magnitude smaller than X" |
| "robust results" | "positive in 95% of draws" |
| "large welfare gain" | "$\Delta W = 0.83$ (95% CI: $[-0.02, 3.22]$)" |

### Sign convention: define once, use everywhere

Pick a sign convention and state it explicitly:
```
We define $\Delta W = W_{\text{IB}} - W_{\text{flat}}$, so positive values
indicate income-based fines dominate.
```

Then verify every sentence, table, and code comment uses the same convention. This was the single most common source of internal contradiction across review rounds.

### Conservative framing

When a modeling choice makes your results *harder* to obtain, say so explicitly and explain why it strengthens the conclusion:

```
WEAK: "Our Frisch elasticity of 1.0 is higher than the consensus of 0.25."
STRONG: "Our quadratic disutility implies a Frisch elasticity of 1.0—four times
the empirical consensus of 0.25. Since the labor distortion is increasing in
the elasticity, income-based fines would dominate even more strongly at realistic
elasticities. The finding that income-based fines dominate in 95% of draws
despite an elasticity four times the consensus strengthens the qualitative
conclusion."
```

### Derive, don't assert

If a parameter has a non-obvious value, show the algebra:

```
The Frisch elasticity is $\varepsilon^F = v'(h) / [h \cdot v''(h)]$.
For $v(h) = \frac{\beta}{2}(h/H)^2$, we have $v'(h) = \beta h / H^2$
and $v''(h) = \beta / H^2$, so $\varepsilon^F = 1$.
```

Referees will catch unstated implications. If a functional form pins down a parameter value, derive it explicitly.

### Internal consistency checklist

Before each review round, verify:
1. **Numbers match `results.json`** — grep for all numerical claims
2. **Sign convention is consistent** — check every $\Delta W$ statement
3. **No contradictions across sections** — especially Discussion vs. Conclusion
4. **Citations exist in `.bib`** — every `{cite}` key resolves
5. **Acronyms defined on first use** — EITC, FICA, SNAP, MTR, EMTR, VSL, etc.
6. **Equations numbered and referenced** — no orphan equations
7. **Findings numbered sequentially** — Finding 1, Finding 2, ...

### Cross-section contradictions

The most subtle bugs are claims in one section that contradict another. Common patterns:
- Discussion qualifies a result that Conclusion states unconditionally
- Introduction previews numbers that changed after recalibration
- Calibration states a parameter value that Results uses differently
- "We find X" in one place, "X does not hold" elsewhere referring to the same thing

### Active voice and attribution

Economics journals expect active voice:
```
WRONG: "It was found that income-based fines dominate."
RIGHT: "We find that income-based fines dominate."
```

Cite authors as subjects:
```
WRONG: "It has been shown that the ETI is approximately 0.25."
RIGHT: "{cite}`chetty2012` estimates the ETI at approximately 0.25."
```

### Solo vs. co-authored

- Solo-authored: "I" is clearest, but editorial "we" is standard in economics
  (Saez, Feldstein, Chetty all use "we" in solo papers)
- Pick one and be consistent throughout
- If a referee flags "we" in a solo paper, point to field convention

## Economics/public finance paper structure

Standard structure for a calibrated simulation paper:

1. **Introduction** — motivation, mechanism, contributions (numbered), preview of results, roadmap
2. **Literature review** — organized by subfield, ending with "Synthesis" identifying the gap
3. **Model** — preferences, budget constraint, FOCs, propositions with proof sketches, equilibrium definition, welfare functions, decomposition
4. **Calibration** — data sources, parameter priors (table), Monte Carlo procedure, sample size justification (SE formula)
5. **Results** — numbered Findings, each with italicized formal statement, then interpretation
6. **Discussion** — sensitivity, institutional context, alternative instruments, limitations (be candid), broader implications
7. **Conclusion** — summary, policy implications, future work, concluding remarks

### Propositions and findings

State propositions formally and provide proof sketches:
```
**Proposition 1.** *Under income-based fines, the effective marginal tax rate
on labor income is $\tau + \phi s_i$.*
```

Number findings in Results and italicize the formal statement:
```
**Finding 1.** *Income-based fines generate higher utilitarian welfare than
flat fines in 95% of Monte Carlo draws.*
```

### Limitations section

Be thorough and honest. For each limitation:
1. State the simplification
2. Explain the direction of bias
3. Argue why it doesn't invalidate the main result (if it doesn't)

Referees respect candor and punish hand-waving.

### Standard error justification

For Monte Carlo sample sizes, provide the SE formula:
```
The standard error of $\hat{p} = 0.95$ is
$\sqrt{0.95 \times 0.05 / 100} \approx 0.022$, adequate to establish the
direction of the welfare comparison.
```
