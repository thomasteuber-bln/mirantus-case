# 04 — Prototype brief: Flow A

Input for the Design artifact in step 5. One flow only. Source: `output/03-decision-memo.md`. Rules are quoted from `data/constraints.md`, which I re-read before writing this copy.

## Goal of the prototype
Show one customer with an `unremarkable` result going from the ophthalmologist's evaluation to booking a second screening at the same optician. Test whether customers understand the interval and accept the reminder.

## Who and where
- **Customer:** first screening done; result `unremarkable`; customer-facing copy in German, because the report is German only today.
- **Ophthalmologist:** fills one new field.
- **Optician:** has opted in. Their name is on every customer-facing screen. No extra work for their staff.
- Placeholders: `[Optiker]` (store name), `[Ärztin]` (evaluating ophthalmologist), `[N]` (interval in months), `[Datum]`.

## Screens (one clickable path)

**1. Ophthalmologist evaluation form, new field**
- The existing form, plus a dropdown "Empfohlenes nächstes Screening": 12 / 24 / 36 Monate / keine Angabe. It is required before submitting.
- No default value. The interval must come from the ophthalmologist ("must come from the ophthalmologist's evaluation, not from marketing copy").

**2. E-mail "Ihr Ergebnis ist da"** (service message, so it is allowed without consent)
- Sender name: `[Optiker]` with mira.
- Subject: "Ihr Augen-Screening bei [Optiker]: Ihr Befund ist da"
- Body: "Ihr Befund von [Ärztin] liegt bereit. [Ärztin] empfiehlt Ihr nächstes Screening in [N] Monaten."
- Button: "Befund ansehen"
- **Consent re-ask.** Shown only if `marketing_consent` = false. The checkbox is unticked: "☐ Ja, [Optiker] darf mich per E-Mail erinnern, wenn mein nächstes Screening fällig ist." Below it: "Sie können das jederzeit abbestellen."
- The e-mail contains no result itself.

**3. Report, page 1, new box at the top**
- "Nächstes Screening: in [N] Monaten, empfohlen von [Ärztin]."
- "Ein unauffälliger Befund zeigt den heutigen Stand. Ein regelmäßiges Screening hilft, Veränderungen früh zu sehen."
- Footer line: "mira ist ein nicht-medizinisches Screening und ersetzt keine augenärztliche Untersuchung."
- The rest of the report stays as it is.

**4. Reminder e-mail at the due date** (consenting customers only)
- Sender name: `[Optiker]`.
- Subject: "Ihr nächstes Augen-Screening bei [Optiker]"
- Body: "Am [Datum] waren Sie bei uns zum Augen-Screening. [Ärztin] hat damals empfohlen, nach [N] Monaten wiederzukommen. Dieser Zeitpunkt ist jetzt."
- Button: "Termin bei [Optiker] buchen"
- Footer: unsubscribe link.
- *Copy variant for the back-catalogue test only* (same screen, no interval exists for these customers): "Am [Datum] waren Sie bei uns zum Augen-Screening. Möchten Sie einen neuen Termin vereinbaren?" No interval and no medical claim.

**5. Booking page**
- Pre-set to `[Optiker]`'s location, showing free slots. Confirm. This is followed by the existing booking confirmation e-mail.

## Copy rules (from `data/constraints.md`)
- "No fear-based messaging ("you could go blind")." No words like Risiko, Erblindung, Gefahr.
- The interval appears only where `[Ärztin]` set it, and always attributed to her.
- No diagnosis or treatment language outside the report.
- No reminder without consent: screen 4 is unreachable in the prototype when consent = false.
- The optician's name is on screens 2, 4 and 5 ("on the optician's behalf and with the optician's name on it").

## Out of scope
Flow B (due list), SMS/WhatsApp, translations, discounts, risk-factor questions, and any second flow.

## What to observe with test customers
- After screen 3, can they say when to come back, and who said so?
- On screen 2, do they tick the consent box, and why or why not?
- On screen 4, does the sender feel familiar? Does it feel pushy? (The optician interview says older customers may find it pushy. Keep this contradiction open.)
