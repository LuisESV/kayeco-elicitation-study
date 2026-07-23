# Kay.Eco Elicitation Study

**Preference elicitation via an AI interviewer on a real, non-captive population: a
preliminary external-validity datapoint for agent-run marketplaces.**

---

## Abstract

Anthropic's *Project Deal* showed that preferences elicited from people by a Claude
interview can be compiled into agents that transact on those people's behalf, but it
elicited them from 69 frontier-AI-lab employees in a controlled internal setting. This
study asks whether the *elicitation step* survives contact with a real, non-captive
population: external users interviewed by an SMS concierge about their own professional
goals, in the wild, over several weeks (two cohorts of 16 and 29 users, 13 of them
returning from the first). We find that real
strangers readily disclose rich, multi-dimensional, and often *quantified* preferences
to an AI interviewer (price points, budget thresholds, transaction fees, and hard
qualifying constraints), frequently *unprompted*, and that willingness to disclose
**exceeds** what the capture pipeline actually structured. This is descriptive evidence
about elicitation feasibility and richness only; it does not test negotiation, matching
quality, or transaction outcomes.

---

## Motivation

Agent-run marketplaces depend on a step that is easy to take for granted: getting a
real person's preferences *into* the agent that will act for them. Anthropic's **Project
Deal** is the strongest existing demonstration that this can work end-to-end: it
elicited each participant's buy/sell preferences through a Claude interview, turned that
interview into a custom agent system prompt, and let the agents transact. Its structural
limit as evidence is the **elicitation population and setting**: 69 Anthropic employees
(AI-fluent, cooperative, incentivized) interviewed in a controlled internal channel over
low-stakes personal goods.

*Does the elicitation step generalize beyond a captive, AI-friendly population at low
stakes?* Kay.Eco is a direct,
if smaller, test of exactly that step on the population Project Deal could not reach:
founders, operators, and professionals, over SMS, about their own business-development
goals. **It does not test transaction or negotiation** (Project Deal owns that); it tests
**whether real people will disclose usable preferences to an AI at all, and how much.**

Kay is an SMS concierge that interviews users about their professional goals and connects
them with other users. It ran two cohorts: **Cohort 1** (16 users, fixed questions) and
**Cohort 2** (29 active users, dynamic gap-driven questions). The elicitation-relevant
evidence is almost entirely from Cohort 2: larger, more open conversation, richer
disclosure.

**Comparability caveat, stated up front.** The two cohorts ran on very different
timelines (Cohort 1 was a tight 5-day window; Cohort 2 ran across roughly three weeks
with restarts). Per-day or "retention-over-time" comparisons between them are **not
reliable** and are avoided here. The evidence below is about **depth and willingness of
disclosure**, which is timeline-robust.

---

## Method

**Recruitment.** Participants were drawn primarily from a Kay.Eco waiting list: people
who had submitted an interest form agreeing to be contacted about participating in
Kay.Eco. Both cohorts were opt-in; participants joined to try the service and receive
introductions.

**The interview.** Kay is an SMS concierge that interviews a user about their
professional goals and then connects them with other users. The question protocol
differed between cohorts:

- **Cohort 1 (fixed).** A preset sequence of questions delivered over about 4 days, the same
  schedule for everyone.
- **Cohort 2 (dynamic, gap-driven).** Instead of a fixed script, the system generated
  questions to close **matching gaps**: specific pieces of information missing between
  two candidate participants. Two profiles can look compatible at the surface while
  diverging underneath (for instance, two users who both list "wellness" may mean very
  different things: one a clinical-health focus, the other a lifestyle or product
  focus, implying very different ideal counterparts). Over roughly three weeks the
  interviewer generated and asked targeted follow-ups to resolve these gaps, and
  delivered an introduction when a viable match was found. Questions served matching, not
  the reverse.

**Dates.** Cohort 1 ran **Feb 13–18, 2026**; Cohort 2 ran **Mar 25 – Apr 8, 2026**.

**Models.** Kay's interviewer and matching pipeline were powered by **OpenAI models**.
This study is about the elicitation *step* on a real population and is independent of
which model conducts the interview.

- *Cohort 1:* a substance-scoring layer (`gpt-4o-mini`) assessed whether two people could
  help each other (skills, network, and goal alignment), and a reasoning-heavier layer
  (`o3-mini`) handled the harder matching judgments.
- *Cohort 2:* `gpt-4o` was the primary model for the matching cascade (short- and
  long-term gap resolution, personality matching, match criticism, and the core scoring
  logic); `gpt-4o-mini` handled lightweight tasks (question generation, clarification,
  first-pass contextualization), with `gpt-4o` as a fallback when the lighter model
  failed.

**Consent and scope of publication.** Participants consented to the use of their
information for **product testing and outreach by email and mobile**, and opted in to try
the service to receive introductions. This repository publishes **only anonymized,
aggregate statistics that cannot identify an individual**: no roster, no contact
information, no verbatim messages. Inviting participants into formal research would be
handled through a separate, explicit opt-in; nothing here depends on or asserts such
consent.

---

## Results

Throughout, participants are referred to by stable pseudonyms (P1, P2, …). Disclosures
are **paraphrased** (described by *what* was disclosed, not reproduced verbatim), and
internal line references to the transcript corpus are shown as "internal transcript
reference." Aggregate tables backing every count are in [`tables/`](tables/).

### Evidence 1: Elicitation is feasible on a real, non-captive population

Real users engaged with an AI interviewer and came back for a second round unprompted.

| Measure | Value |
|---|---|
| Cohort-1 users who re-enrolled in Cohort 2 (voluntary carryover) | **13 / 16 = 81%** |
| Users who engaged the question phase (Cohort 2) | 22 / 29 = 76% |
| Users who volunteered substantive info beyond answering questions (Cohort 2) | 22 / 29 = 76% |
| Users with ≥1 "burst" session (Cohort 2) | 23 / 29 = 79% |
| Users who sent ≥1 message (Cohort 1 / Cohort 2) | 94% / 97% |

**Read:** an AI interviewer reached real strangers over SMS, about three-quarters actively
participated, and **81% who tried it once chose to come back**, a retention signal on a
non-captive population that Project Deal's incentivized internal setting could not
observe. See [`tables/engagement_rates.csv`](tables/engagement_rates.csv).

### Evidence 2: What users disclose is rich and multi-dimensional

Elicitation produced structured, per-person preference signal well beyond a résumé.

- **Answered-question signal:** users who engaged answered about 3 targeted questions each
  (Cohort 2 mean 3.0, Cohort 1 mean 3.5); 57 structured Q&A answers total in Cohort 2.
- **Dimensions per engaged user:** on top of a public professional profile, engaged users
  carried roughly **3–14 conversation-extracted preference dimensions** (needs, offers,
  goal corrections, context), clustering **6–14 for the 16 richest-signal users**.
- **Elicitation cost is low:** the whole interview averages **about 12 minutes per user**
  across about 4 short bursts (average burst about 4.8 messages / 7 minutes / 57 words).

**Read:** a lightweight AI interview elicits a multi-dimensional preference profile per
person at low time cost: the raw material an agent needs to act on someone's behalf. The
*captured* count is a **floor**, not a ceiling (see Evidence 4). See
[`tables/disclosure_counts.csv`](tables/disclosure_counts.csv).

### Evidence 3: Users volunteer *specific, quantified* preferences

The strongest signal: unprompted, real users disclosed **numeric, incentive-relevant
preferences** (the same class of information Project Deal had to elicit in a controlled
interview) to a text bot, about strangers they wanted to be matched with. Each entry
below paraphrases what the user volunteered; none is a verbatim quote.

- **P1:** Willingness to pay finder's fees to partners who refer business.
- **P2:** A target customer defined by a minimum funding threshold (about $1M raised); a
  monthly subscription price point his customers would pay (about $50/month); and an
  annual-recurring-revenue goal for his platform (about $400K ARR).
- **P3:** The investor profile he wants, as a check-size range (about $100K–$2M), plus the
  size of the round he is actively raising (about $2.3M).
- **P4:** A detailed target-counterpart persona defined by nationality, wealth level, and
  life stage, oriented to a luxury segment.
- **P5:** The commercial relationship he wants (paid pilots), the counterpart
  organization type and size, a geographic constraint, and the seniority of titles to
  target.
- **P6:** A target-company persona by funding stage, geography, and investor /
  accelerator pedigree.

**Read:** these are price points, budget thresholds, transaction fees, and hard
qualifying constraints, volunteered without being asked, at real professional stakes, by
people who are not Anthropic employees. This is the direct evidence that the elicitation
step underpinning Project Deal generalizes: **real users will tell an AI the quantified,
incentive-relevant preferences needed to represent them.**

### Evidence 4: Willingness to disclose *exceeds* what the system captured (a lower bound)

Kay's extraction pipeline was deliberately conservative and structured only a fraction of
what users volunteered. The gap is not a limitation of the *thesis*; it is a **lower
bound on human willingness to disclose.**

| Channel | Disclosures | Captured as structured signal |
|---|---:|---:|
| Answered questions (targeted) | 57 | 57 |
| **Volunteered, unprompted** (>5-word non-answer shares) | **153** | **23** |
| **Total preference-bearing disclosures** | **210** | **80** |

- Voluntary-channel capture rate: **23 / 153 = 15%.**
- **about 130 volunteered preference-shares were expressed but never converted to usable
  signal.**
- The uncaptured slice includes roughly **12 explicit target-persona specifications,
  15 needs↔offers corrections, and 20 detailed business-context disclosures.**

**Concrete illustration.** One user (**P7**) told the interviewer he wanted connections
within a specific ethnic community, including in technical roles; the system delivered a
match the next day that did not reflect this attribute, because the stated preference was
never structured (internal transcript reference). The preference existed and was
volunteered; the pipeline simply didn't use it.

**Read:** even a system that structured only 15% of volunteered input still surfaced
quantified preferences and hard constraints. **True willingness to disclose to an AI
interviewer is materially higher than what the current capture pipeline structured.** For
a marketplace-of-agents research agenda, this quantifies a *latent supply of preference
data*: the opportunity, not a defect. See
[`tables/expressed_vs_captured.csv`](tables/expressed_vs_captured.csv).

---

## Limitations

This was a product experiment, not a study designed for research, hence some of the
limitations below. It doesn't change the direction of the results.

- **Small, single-operator cohorts.** Two cohorts (16 and 29 users) run by one product;
  descriptive statistics only, no control group, no significance testing.
- **Cohorts are not directly comparable over time.** Different timelines and restarts
  mean retention-over-time comparisons are unreliable; only timeline-robust
  disclosure-depth measures are used.
- **Capture rate is a property of one pipeline.** The 15% voluntary-capture figure
  reflects Kay's deliberately conservative extraction at the time; it is used as a lower
  bound on willingness, not as a fixed property of AI elicitation.
- **Selection.** Participants opted into a networking concierge and had their own
  business-development goals, which plausibly raises willingness to disclose relative to a
  general population.
- **Self-report.** Disclosures are what users *said* they want; this study does not
  verify them against behavior.
- **No matching-quality or outcome claims.** Match success, negotiation, and downstream
  value are explicitly out of scope.

---

## Data availability

The underlying SMS transcripts contain personally identifiable information (names, phone
numbers, employers, and other identifying detail) and are **not published**. The
aggregate tables in this repository are derived from anonymized extracts of those
transcripts: participant names are replaced with stable pseudonyms, verbatim quotes are
paraphrased into descriptions of what was disclosed, and internal line citations are
removed. The anonymized extracts underlying these aggregates are available to researchers
on reasonable request.

---

## License

The research note and aggregate tables in this repository are licensed under
[CC BY 4.0](LICENSE).
