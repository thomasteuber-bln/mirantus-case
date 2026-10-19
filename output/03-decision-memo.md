# Decision memo: bring "unremarkable" customers back

Data is synthetic. Every number comes from `output/01-cohort.md`.

## The problem
Of the 5,773 customers who have had a full year to return, 287 came back: **5.0%**. The biggest leak is customers whose result was `unremarkable`. They are 3,995 customers (69%) and return at **3.5%**, against **10.1%** for `minor_findings`. That is 265 returns short, and the gap holds within every follow-up type, age band and report-opened group.

Today nothing tells them to come back. The report has no return interval, and after an unremarkable result there is "no further contact" (customer-journey.md). A customer, 67: "Warum? War doch alles in Ordnung." The ophthalmologist: "Patients read it as 'I'm healthy'."

## The decision
**Flow A: the ophthalmologist sets the interval, and the optician's name carries the reminder.**
- **Evaluation form:** a new "next screening in N months" field, filled in by the evaluating ophthalmologist. She "would fill it in if it were there."
- **Report and "Your result is ready" e-mail:** the interval in plain German, under the optician's name.
- **Consent re-ask:** in that same result e-mail, for customers who did not give `marketing_consent`. It is a message they already receive legitimately.
- **Reminder e-mail at the due date:** consenting customers only, sent on the optician's behalf with the optician's name, linking to booking at that store.
- **Opticians opt in.** No extra work for them. At chains, opt-in goes through HQ (survey answer S7).

## Ships in the next two weeks
The interval field, the report line, the result-e-mail copy with the consent re-ask, the reminder e-mail template, and the optician opt-in.

## Cut
- "Due this month" list for opticians (Flow B).
- SMS/WhatsApp. Constraints name only the PDF and e-mails as changeable.
- English or plain-language report.
- Second-screening discount.
- Risk-factor questions at the screening.
- Posters.
- Examiner training.

## Success metric
**Primary:** second-screening return rate for `unremarkable` customers in the eligible cohort (at least 12 months since first screening). The baseline is 3.5% and the comparator is 10.1%.

**Leading indicators**, which can be read early:
- consent opt-in from the result e-mail, among the 2,611 eligible customers without consent;
- bookings from the reminder e-mail;
- report open rate, with a baseline of 3,778 of 5,773 eligible customers.

## Guardrails
- No reminder goes to a customer without consent.
- No interval appears unless the ophthalmologist set it.
- No fear-based copy.
- Report open rate does not fall.
- Unsubscribes and optician opt-outs stay low. Threshold not in the data; set it before launch.
- The referral flow is untouched (`referral_booked` 4.9% vs 3.6% not booked).

## Test with real users inside two weeks
- **New screenings at opted-in opticians:** the ophthalmologist fills in the interval, and customers get the new report and result e-mail. Measure consent opt-in and report opens against the same opticians' prior customers. Call back a handful of customers to check that they understood the interval.
- **Back-catalogue:** take consenting `unremarkable` customers at opted-in opticians who are past 12 months and have not returned. Randomly split them into a reminder group and a holdout. The reminder states only the date of the last screening and the optician's name, with no interval and no medical claim. Measure bookings in each group within the two weeks.

**Decision rule:** ship to all opted-in opticians if reminder bookings beat the holdout and no guardrail breaks.
