# 02 — Synthesis

Sources: 4 interviews (`data/interviews/01`–`04`), 15 optician survey answers (`data/optician-survey.md`, cited as S1–S15), `data/customer-journey.md`, `data/constraints.md`, `output/01-cohort.md`. All data is synthetic. Numbers come only from `output/01-cohort.md`. No personas, no recommendation.

## 1. Constraints (from `data/constraints.md`, quoted)

- Consent: "Customers may only receive reminders or marketing if they gave `marketing_consent` at booking." Without it, only messages "needed to deliver the service already bought". Consent "can be asked for again later, but only in a message the customer already receives legitimately, or in person."
- Medical: "Recommending a screening interval to a specific customer counts as a medical statement: it must come from the ophthalmologist's evaluation, not from marketing copy." "No fear-based messaging."
- Relationship: "Mirantus may contact customers only for the service itself, or on the optician's behalf and with the optician's name on it." "Opticians can't be required to do extra work, but they can be offered tools."
- Capacity: "One squad for one quarter: 2 engineers, 1 designer, you." "The report PDF and e-mails can be changed. The opticians' own systems (their CRMs, cash registers) can't be integrated this quarter."

## 2. Journey drop-off

The main leak from step 1: `unremarkable` customers, 3,995 of 5,773 eligible (69%), return at 3.5% vs 10.1% for `minor_findings`.

Where the journey goes quiet for them (`data/customer-journey.md`):
1. E-mail 3 "Your result is ready" carries no result, only a login link. 1,995 eligible customers never opened the report; they return at 2.2% vs 6.4% for openers.
2. The report is 4 pages, German only, "in medical language", and has **no** recommendation for when to come back.
3. After an unremarkable or minor result: "**no further contact** from Mirantus." Any follow-up depends on the optician; 3,192 eligible customers are at locations reporting `none` (4.1% return vs 8.3% for `phone`).

So the drop-off point is the report itself and the silence after it. No step in today's journey tells an unremarkable customer to come back, or reminds them.

## 3. Themes with two or more sources

**T1. "Unremarkable" is read as "done".**
- Customer, 67: "Warum? War doch alles in Ordnung."
- Ophthalmologist: "An unremarkable result is a snapshot, not a guarantee. Patients read it as 'I'm healthy'." and "It's the 'unremarkable' 60-year-olds who disappear."
- Cohort: unremarkable 3.5% vs minor_findings 10.1%, gap holds within every follow-up type, age band and report-opened group.

**T2. The report has no return interval, and the ophthalmologist would give one.**
- Journey: the report has "**no** recommendation for when to come back".
- Ophthalmologist: the form "has no field for a recommended interval. I would fill it in if it were there. It takes five seconds."
- S6: "Wenn im Befund steht 'Nächstes Screening in 12 Monaten', dann glauben die Leute das auch."

**T3. A trusted person's prompt brings people back.**
- Customer, 67: "Wenn Herr K. sagt, ich soll wieder kommen, dann komm ich wieder."
- Customer, 44: "Honestly I'd love a reminder. Just WhatsApp me in a year. I will forget otherwise."
- Cohort: optician `phone` follow-up 8.3% vs `none` 4.1%.

**T4. Consent given, nothing sent.**
- Customer, 44: ticked the reminders box; "Has received nothing since the report."
- Journey: no further contact after unremarkable/minor results.
- Cohort: consent true 6.0% vs false 3.7%. Share of consenting customers within `unremarkable`: not in the data (not cut in 01-cohort.md).

**T5. The report is hard to read, and language blocks opening.**
- Customer, 44: Google Translate, "half of it made no sense"; wants it "in English and in normal words".
- Customer, 67: "Da standen lauter Fachbegriffe drin."
- Ophthalmologist: "They are written for colleagues, honestly. Not for patients."
- Cohort: report open rate de 71.7% vs non-de 37.3%; among openers the language gap is 0.4 pp.

**T6. Opticians want customer contact under their own name.**
- Optician, Bavaria: "The customers are mine. If someone writes to them, it's me."
- S1 ("mit unserem Logo"), S4 ("Bitte keine Mails von Mirantus an meine Kunden"), S11 ("Der Befund sollte von uns kommen").
- Customer, 67: doesn't remember Mirantus; calls it "der Augen-Check bei Herrn K."

**T7. Opticians lack time and staff for manual follow-up.**
- Optician, Bavaria: "aber wer soll sich das merken?"; trained examiner left, screenings near zero for 6 weeks.
- S9 ("Wir haben keine Zeit, Kunden anzurufen. Es muss automatisch gehen."), S12 (lost trained person).

**T8. Price of a yearly repeat.**
- Customer, 67: "für einmal okay, aber jedes Jahr? Weiß ich nicht."
- S5: "69 € every year is a lot for pensioners."

**T9. E-mail is a weak channel for some customers.**
- Customer, 67: reads e-mail "ab und zu"; uses WhatsApp.
- Customer, 44: "Just WhatsApp me".
- S14: "SMS statt E-Mail. Unsere Kunden lesen keine E-Mails."
- Note: constraints name only "the report PDF and e-mails" as changeable. SMS/WhatsApp: not in the data.

**T10. Risk factors are not captured.**
- Customer, 67: sister has glaucoma; "nobody asked".
- Ophthalmologist: risk factors "aren't asked at the screening, so she often can't tell who should come back sooner."

## 4. Contradictions (kept, not merged)

- **Who the reminder should come from.** Customer, 44: "But not from the optician. I don't even remember which store it was. I'd want it from whoever has my results." vs. Customer, 67 (comes back if Herr K. says so), Optician, Bavaria, S1, S4, S11 (from the optician). Constraint: Mirantus may only contact "on the optician's behalf and with the optician's name on it".
- **Will opticians call?** S3 and Optician, Bavaria: "A list. Who should come back this month. Then my people can call." vs. S9 "Wir haben keine Zeit" and the same optician: "wer soll sich das merken?"
- **Do customers want to be reminded?** Customer, 44: "I'd love a reminder." vs. Optician, Bavaria: "Older customers find it pushy if you call them for something they didn't ask for." vs. Customer, 67 (the older customer): would come back if asked by her optician.
- **Is there a return problem at all?** S2: "Nothing, our customers come back for glasses anyway." vs. cohort: 5.0% eligible return rate. Optician, Bavaria, on her own data: "a few" came back, "can't say how many".
- **What the optician gets out of it.** S13: "Interessant ist es nur, wenn danach eine Brille verkauft wird." vs. Optician, Bavaria: it also "unterscheidet uns von der Kette nebenan."
- **Who decides.** S7: at chains, "HQ decides about customer communication, not the store." Other answers assume the store decides.

## 5. Candidate flows (at most two, not ranked)

Both target `unremarkable` customers and both depend on T2: the interval must come from the ophthalmologist's evaluation.

**Flow A — Interval in the report + optician-branded reminder e-mail.**
1. Ophthalmologist fills a new "next screening in N months" field on the evaluation form.
2. The report and the "Your result is ready" e-mail state that interval in plain words, with the optician's name.
3. Customers without consent are asked for it in that e-mail (a message they already receive legitimately).
4. At the due date, consenting customers get a reminder e-mail sent on the optician's behalf, with the optician's name, booking link to that store.
- Uses only changeable surfaces (report PDF, e-mails). No extra optician work.
- Open: chains may need HQ sign-off (S7); e-mail reach (T9); price (T8).

**Flow B — Interval in the report + "due this month" list for the optician.**
1. Same as A, steps 1–2.
2. The optician gets a monthly list of their consenting customers whose interval is due; their staff contact them.
- Matches S3 and the Bavaria optician's wish; phone follow-up has the highest return rate in step 1 (8.3%).
- Open: depends on staff time (S9, T7); cannot integrate into optician CRMs this quarter; whether a Mirantus optician dashboard exists today is not in the data.
