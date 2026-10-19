## How to rerun

Clone the repository and start Claude Code inside it. Run one step from `workflow.md` at a time, and answer at each stop before the next step starts.

```bash
git clone https://github.com/thomasteuber-bln/mirantus-case.git
cd mirantus-case
claude
```

The cohort agent must already be at `.claude/agents/cohort.md`. Step 2 uses the `product-management:synthesize-research` skill. If not installed yet, it is available via https://github.com/anthropics/knowledge-work-plugins/tree/main/product-management 

First message:

```text
Run workflow.md step 1. Stop at the checkpoint.
```

Then:

1. Read `output/01-cohort.md`. Reply with whether the metric and the drop-off are right. Step 2 does not start until you do.
2. Read `output/02-synthesis.md`. Reply with which one flow the memo should use.
3. Let steps 3 and 4 write the memo and the prototype brief.
4. When `output/04-prototype-brief.md` exists, tell Claude to build one clickable flow with the Design artifact. Save the link in `output/05-prototype.md`.

When one input changes, delete the output files of the steps you rerun.

/export function is not available in Claude Code Desktop, so the transcript is the session logs.
