# Verdict format

Use this for Council and Forge runs. For Quick, keep only Answer, Evidence and What would flip it.

```markdown
## Verdict
<The answer in 1–2 sentences. If it depends on a condition, name the condition.>
Confidence: high / medium / low, because <reason>.

## Why
| # | Claim | Evidence | Type |
|---|-------|----------|------|
| 1 | ... | [source](url), "exact figure or passage" | sourced |
| 2 | ... | benchmark: 41ms → 29ms (n=5) | tested |
| 3 | ... | follows from 1 + 2 | inferred |
| 4 | ... | user said team is 3 people | assumed |

## The best case against
<The strongest opposing argument from the Breaker or the clash, and why it didn't win.
If it nearly won, say so.>

## What would flip it
- <Observation> → would change the answer to <X>. Cheapest check: <how>.

## Options considered
| Option | Verdict | Key reason |
|--------|---------|------------|

## Run log
Mode: Council · Agents: 4 independent (Builder, Breaker, Tester, Outsider)
Searches: ~N · Experiments: N · Clash rounds: N
Skipped / blocked: <anything that didn't run, and why>
Unverified: <claims you couldn't check>
```

## Evidence labels

- **sourced**: you opened the source and confirmed the passage applies here.
- **tested**: you ran it and observed the result yourself.
- **inferred**: your reasoning from the items above.
- **assumed**: given by the user or taken as true without checking.

Never upgrade a label. A claim found in a search snippet that you didn't open is not "sourced".
