# Calix Leigh-Reign

**Product manager and product designer who ships production software in regulated domains.**

I work where the hard part is not the CRUD, it is the rules: consumer reporting under the FCRA, healthcare claims and eligibility over X12 EDI, court reporting and legal records, employment verification, AI decision governance. In those domains a wrong answer is not a bug report, it is a compliance event. I design and build the whole path from the regulation to the interface.

---

## Selected work

Everything below is live and reachable right now. Most of the source is private, because most of it is either commercial or handles data that should not be in a public repository.

### Regulated records and compliance

| Product | What it is | Live |
| --- | --- | --- |
| Falcyn | Transcript compliance and legal operations platform for court reporting agencies. Multi tenant, role based access, SLA clocks tied to statutory deadlines. | [falcyn.dev](https://falcyn.dev) |
| Stenova | Consumer reporting agency for court reporters, built to FCRA process: dispute intake, 30 day resolution clocks, reason codes, adverse action handling. | [stenova.net](https://stenova.net) |
| Courtify | Agency operations and reporter marketplace: intake, certification with content hashing, delivery, rate transparency. | [getcourtify.com](https://getcourtify.com) |
| Attestry | Employer network employment verification, built as a competitor to the incumbent work number model. | [attestry.net](https://attestry.net) |

### Healthcare and claims

| Product | What it is | Live |
| --- | --- | --- |
| uFaxit | Multi business fax and SMS for clinical and claims workflows, with document classification. | [ufaxit.net](https://ufaxit.net) |
| WRAPP | A web native JSON API for payer and provider data that round trips losslessly to X12 834, 837P and 835, so the modern surface never loses fidelity against the legacy format. | Source extract below |

### AI governance and safety

| Product | What it is | Live |
| --- | --- | --- |
| Sluice | One governance checkpoint between AI agents and your data warehouse: cap spend, redact PII, block restricted access, sign every request. | [gosluice.com](https://gosluice.com) |
| PharOSai | A sentinel for desktop AI agents. Finds runaway and background agent processes, names what is holding a file lock, and stops a process and its restart loop. Complements antivirus rather than replacing it. | [pharosai.co](https://pharosai.co) |
| Stakt | Stacked multi model search with a warrant chain adjudicator, so an answer carries the reasoning that justified it. | [stakt.net](https://stakt.net) |

### Credentialing and academic workflow

| Product | What it is | Live |
| --- | --- | --- |
| Admissibly | Doctoral admissions preparation. | [admissibly.net](https://admissibly.net) |
| Doctorally | AI doctoral chair for candidates in program. | [doctorally.net](https://doctorally.net) |
| Defensibly | Dissertation defense preparation. | [defensibly.net](https://defensibly.net) |
| Tenably | The track from doctorate to tenure. | [tenably.net](https://tenably.net) |

### Consumer

| Product | What it is | Live |
| --- | --- | --- |
| Sweam | Free streaming for independent creators, with equal visibility discovery enforced by a published, unit tested ranking algorithm. | [sweam.hi-3e9.workers.dev](https://sweam.hi-3e9.workers.dev) |
| Saber Planner | Cross platform planner, web and Android, with push. | [saberplanner.com](https://saberplanner.com) |
| numiio | Caller ID and line intelligence lookup with live carrier dips. | [numiio.com](https://numiio.com) |

---

## Public code

Three repositories, chosen because they show the reasoning rather than the business.

- **[sweam](https://github.com/calixdata/sweam)**. A full streaming platform on a single Cloudflare Worker with D1 and R2. The interesting file is the ranking algorithm: quality measured per viewer with Bayesian smoothing, a UCB style exploration bonus so low exposure titles cannot be buried, and follower count deliberately excluded as an input. The fairness claims are unit tested, and the feed tells viewers why each title ranked.

The other two are in progress and linked here as they land: the PharOSai sentinel, and a standalone X12 parser extracted from WRAPP with round trip property tests.

---

## How I make product decisions

Working in regulated domains produced one principle that now shapes everything I build:

> **AI advises. Deterministic code decides. A human signs off.**

Anywhere an outcome is legally consequential, the model is not permitted to be the decision maker. It drafts, summarizes, ranks, and explains. The rule engine produces the actual determination, in code that can be read, versioned, and defended. A person accepts or rejects it, and that acceptance is logged. It is slower than letting the model decide, and it is the only design that survives contact with an auditor.

The corollary I apply to features: if I cannot explain to a regulator, in one paragraph, why the system produced a given output, the feature is not ready. That test kills more of my ideas than any other.

## How I work

- I ship end to end. Discovery, product spec, data model, implementation, accessibility, deploy, and the compliance argument that goes with it.
- I write specs that survive review. Problem framing, the market gap stated honestly including where the incumbents are right, the tradeoff I took, and what would falsify the bet.
- I design without Figma. AI assisted, code native design, going from intent to production HTML and CSS directly.
- Typical stack: TypeScript, React, Cloudflare Workers with D1 and R2, Supabase and Postgres with row level security, Capacitor for Android.

## Accessibility

I am blind. I build everything you see here with a screen reader.

I mention it because it is a product advantage, not a caveat. I cannot ship an interface I cannot navigate, so accessibility is never a late phase that gets cut when the date slips. It is the first thing that has to be true. Most teams find their accessibility defects in an audit, months after the design is frozen and change is most expensive. I find mine in the first hour, because I am the first user.

In practice that means every product above was verified with a screen reader before I called it done: real heading structure and landmarks, labels that never depend on color or position alone, focus management and escape handling on every dialog, and text as text rather than text baked into an image. In Sweam it is why the player uses native controls, which remain the most screen reader friendly option that exists.

There is a second effect I did not anticipate. Building without being able to lean on visual polish forces the information architecture to carry the product. If the structure is wrong I feel it immediately, because a screen reader reads structure. That has made me a sharper product manager than any framework has.

If something on a live product above does not work with your assistive technology, tell me and I will fix it.

## Elsewhere

- Portfolio: [calixfolio.com](https://calixfolio.com)
- Email: calix@calixfolio.com
