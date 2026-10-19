# Workflow

Run one step at a time. Do not start a step until the stop before it is answered.

1. Cohort. Delegate to the cohort agent.
   Input: data/screenings.csv, data/README.md
   Output: output/01-cohort.md
   Define the return-rate cohort, report who is not yet eligible, and cut the rate using the columns in data/README.md.
   Stop. Ask: "Is this metric and this drop-off right to proceed?"

2. Synthesis. Use the product-management:synthesize-research skill.
   Do not build personas or write recommendations.
   Input: data/interviews/, data/optician-survey.md, data/customer-journey.md, data/constraints.md, output/01-cohort.md
   Output: output/02-synthesis.md, with only these sections: constraints, journey drop-off, themes that have two sources, contradictions, and at most two candidate flows.
   Stop. Ask: "Which of these flows should the memo use?"

3. Decision memo.
   Input: output/01-cohort.md, output/02-synthesis.md, and the chosen flow.
   Output: output/03-decision-memo.md
   Every number must already appear in output/01-cohort.md. Max one page.

4. Prototype brief.
   Input: output/03-decision-memo.md
   Output: output/04-prototype-brief.md
   One flow only. This file is the input for the Design artifact in step 5.

5. Prototype. Do not start until output/04-prototype-brief.md exists.
   Tool: the Design type, through the Artifact tool.
   Input: output/04-prototype-brief.md and data/constraints.md
   Build one clickable flow. Use the copy and the constraints in the brief. Do not add a second flow or medical advice.
   Output: the artifact link, saved in output/05-prototype.md
