# 🔥 Crucible: Research Council

**Put an idea under heat and see what survives.**

Crucible is an Agent Skill for **Claude Code**, **Claude.ai** and **Codex**. It turns "research this" into a structured fight: four independent sub-agents attack your question from different angles, argue only where they disagree, check the claims that matter, and give you a verdict along with the evidence that would flip it.

```text
Use crucible: should our 3-person team build the MVP on Supabase or a custom
Node + Postgres backend? ~2k users in year one, one backend dev.
```

That's a complete prompt.

## How it works

```
 Frame ──► Council (4 parallel agents) ──► Clash ──► Verify ──► Verdict
            Builder · Breaker ·             only the     check the    answer + evidence
            Tester · Outsider               disagreements key claims   + what would flip it
```

| Agent | Job |
| --- | --- |
| **Builder** | Reasons from first principles. What must be true? |
| **Breaker** | The adversary. Finds the failure case and the counterexample. |
| **Tester** | Designs the cheapest experiment that settles it. |
| **Outsider** | Steals solutions from other fields and other decades. |

They work in **separate contexts** and can't see each other's first drafts, so you get four real perspectives instead of one perspective four times.

## Modes

| Mode | Use for |
| --- | --- |
| **Quick** | Fact checks and narrow, reversible calls. A single agent, fast. |
| **Council** | Consequential or contested decisions. The full four-agent debate. |
| **Forge** | Anything measurable. The council picks the approach, then a bounded loop improves and measures it against a frozen benchmark. |

If you don't pick a mode, Crucible starts with Quick and only moves up to Council when a real unknown survives. You can set limits in plain English: *"council mode, max 10 searches, no code"*.

## Install

**Skills CLI** (Claude Code and Codex):

```sh
npx skills add yashh46/crucible-research-council --skill crucible-research-council 
```

**Claude Code (manual)**:

```sh
git clone https://github.com/yashh46/crucible-research-council.git
cp -R crucible-research-council/skills/crucible-research-council ~/.claude/skills/crucible-research-council
```

Then type `/crucible-research-council <your question>`, or just ask Claude to "dig into" something.

**Codex (manual)**:

```sh
cp -R crucible-research-council/skills/crucible-research-council ~/.claude/skills/crucible-research-council
```

**Claude.ai**: zip the `skills/crucible-research-council` folder and upload it from the Skills section of Claude's settings. In a plain chat with no sub-agents, Crucible plays the four roles one after another and labels them as not independent.

## What you get back

- **Verdict** in one or two sentences, with confidence
- **Evidence table**, with every claim labeled *sourced*, *tested*, *inferred* or *assumed*
- **The best case against**, and why it lost
- **What would flip it**, and the cheapest way to check
- **Run log**: which agents actually ran, searches, experiments, anything skipped

## Repo layout

```
skills/crucible-research-council/
├── SKILL.md              # the core workflow (what Claude reads first)
└── references/
    ├── council.md        # roles, agent briefs, return format, clash rules
    ├── forge.md          # measurable improve-and-measure loop
    └── verdict.md        # report template and evidence labels
examples/prompts.md       # prompts to try
```


## License

MIT
