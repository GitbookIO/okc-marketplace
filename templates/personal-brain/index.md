# Index

This repo belongs to **Maya Chen**. It holds her notes and meetings, and the topic, project and person pages that workflows compile from them. There is no search: start from the page list below, or list a folder.

## Pages

Kept by the Gardener every Monday.

### Topics

- [A Year of Low Tides](topics/a-year-of-low-tides.md): Ilse Brandsma's year on an island off the Frisian coast, about planning by the tide and learning a language by listening, read up to chapter 8.
- [API design](topics/api-design.md): How Maya designs endpoints like the usage API: one pagination style, integer amounts, a beta flag, and the docs page first.
- [Delegation](topics/delegation.md): Handing the riskiest part of the ledger migration to Dev, with a week of pairing and an agreed review, while Maya still isn't sure the riskiest part should leave the lead.
- [Dutch grammar](topics/dutch-grammar.md): Verb-second word order, de and het, separable verbs, hebben or zijn, and when to say u.
- [Idempotency](topics/idempotency.md): Every charge carries an idempotency key and the Ledger refuses a second entry with the same key, so retries are safe, but how many retries is still in dispute.
- [Language learning](topics/language-learning.md): Flashcards every day or months of listening: Femke and A Year of Low Tides disagree, and Maya is doing both.
- [Usage metering](topics/usage-metering.md) (draft): Metering counts a label when it's bought, minus voids within 24 hours, but the month boundary differs between Acme and Bramble.
- [Zero-downtime migrations](topics/zero-downtime-migrations.md): Expand, write to both, backfill, compare, switch, contract, with the order of dual writes and backfill still open for the ledger migration.

### Projects

- [Learning Dutch](projects/learning-dutch.md): Hold a ten-minute conversation in Dutch with Oma in Leeuwarden at Christmas, without switching to English.
- [Ledger migration](projects/ledger-migration.md): Move credits, refunds and two years of invoices into the Ledger, and build invoices from it by 24 November.
- [Usage-based billing](projects/usage-based-billing.md): Charge per label bought instead of a flat volume tier, starting with a beta on 1 December.

### People

- [Dev Okafor](people/dev-okafor.md): Engineer on Payments who builds the ledger migration with Maya and owns its backfill.
- [Felix Grant](people/felix-grant.md) (draft): Maya's contact at Bramble & Co for the usage billing beta.
- [Femke de Vries](people/femke-de-vries.md): Maya's Dutch tutor, with a lesson every Wednesday evening.
- [Ilse Brandsma](people/ilse-brandsma.md): Author of A Year of Low Tides, which Maya is reading.
- [Nadia Petrov](people/nadia-petrov.md): Maya's manager, with a one-on-one every other Thursday.
- [Owen Brandt](people/owen-brandt.md): Finance at Acme, who signs off on the ledger migration's cutover.

## Concepts

- [Topics](topics/): one page per subject, with the current understanding, contradictions between notes, and open questions.
- [Projects](projects/): one page per piece of work with a goal and an end, at work or not, with where it stands and what's next.
- [People](people/): one page per person who comes up in two or more notes or meetings, with recent conversations and open commitments.
- [Digests](digests/): one weekly review per week, with what was captured and the threads still open.

## Records

- [Sources](sources/): one summary per item dropped into the inbox: notes, links, and conversation summaries agents save.
- [Meetings](meetings/): one file per meeting, with its summary and transcript or notes.

## Everything else

- [Inbox](inbox/): drop notes, links and meeting notes here for Ingest inbox to sort. Agents save here too.
- [Archive](archive/): inbox items that have been processed, exactly as they were dropped.
- [Types](types/): one definition per type, with the fields it uses.
- [Workflows](workflows/): the workflows that keep this repo current.
