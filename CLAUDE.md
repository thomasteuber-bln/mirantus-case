# CLAUDE.md

## Context
Mirantus runs mira at opticians. An examiner does a 15-minute screening: vision, retinal images, eye pressure, slit-lamp photos. An ophthalmologist reviews it remotely within 48 hours, and the customer gets a report.
Most customers come once. Eye disease can progress with no symptoms, so prevention depends on a second screening. For the optician, a returning customer is also a returning store visit.
The data in data/ is synthetic. Do not treat any number in it as a real Mirantus figure.

## Goal
Decide the one change that most raises the second-screening return rate.
Say what ships in the next two weeks and what is cut.
Define the success metric, its guardrails, and a test with real users inside two weeks.

## What good looks like
One recommendation, grounded in data/.
One flow. A memo of one page.

## Users
- Customer: already screened once.
- Examiner: runs the screening at the optician.
- Ophthalmologist: evaluates results remotely.
- Optician: owns the store. A returning screening is also a returning store visit.

## Constraints
Read data/constraints.md before any recommendation or customer-facing copy.
If a recommendation conflicts with that file, the file wins.
Do not paraphrase a rule you have not just read.

## Evidence
Use only files in data/.
Do not treat a customer screened less than 12 months before 30.09.2026 as not returned. Report them as not yet eligible.
Keep contradictions between interviews. Do not merge them into one persona.
Quote user feedback. A claim with no support in the files is marked "not in the data".

## Stop rules
Stop after the metric is defined and the main drop-off is identified. Do not propose a solution yet.
Stop again after one flow is chosen. Do not write a prototype before that.
Do not write a roadmap or a second flow.
