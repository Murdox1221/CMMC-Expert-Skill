# Program Status, Clauses, and Rulemaking

**This file goes stale faster than any other in the skill. Search the web before stating anything from it as current.** Treat what follows as orientation — the shape of the program and where the moving parts are — not as today's facts.

## The two rules

**32 CFR Part 170 — the CMMC Program rule.** Effective December 16, 2024. Defines the levels, assessment types, scoping, POA&M rules, affirmations, and the CMMC ecosystem (Cyber AB, C3PAOs, CCPs, CCAs). This is the substantive rule and the right citation for how the program works.

**48 CFR — the acquisition rule.** Effective November 10, 2025. Puts CMMC into contracts via **DFARS 252.204-7021** (the contract clause making CMMC status a condition of award and requiring maintenance through performance) and **DFARS 252.204-7025** (the solicitation provision identifying the required level). This is the rule that made CMMC contractually real.

## Related clauses — renumbered February 2026, so check before citing

The Revolutionary FAR Overhaul (RFO) class deviations took effect **February 1, 2026** and reorganized the cybersecurity clauses. Citing the old numbers is the fastest way to look out of date in front of a client or a prime, and a lot of published guidance still does.

- **DFARS 252.204-7012** — **unchanged.** Safeguarding covered defense information: 800-171 implementation, **72-hour** cyber incident reporting to DoD, media preservation, malicious software submission, flowdown to subcontractors. The FedRAMP Moderate equivalency requirement for cloud lives here. Still the workhorse clause.
- **DFARS 252.204-7019** — **deleted.** The standalone requirement to perform a Basic self-assessment and post the score to SPRS no longer exists as its own provision.
- **DFARS 252.204-7020** — **renumbered to DFARS 252.240-7997** under new DFARS Part 240, and rewritten to drop "Basic" assessments entirely; it now addresses Medium and High assessments, both government-performed.
- **FAR 52.204-21** — **renumbered to FAR 52.240-93**, basic safeguarding of covered contractor information systems. The 15 requirements themselves did not change, and they remain the basis of CMMC Level 1.
- **DFARS 252.204-7021 and 252.204-7025** — unchanged by the RFO; these are the CMMC clause and solicitation provision.

The practical point for clients: the self-assessment obligation was consolidated into CMMC, not eliminated. A contractor with no CMMC clause in its contracts today may still be in breach of 7012, which has been in force since 2017 and was untouched. "CMMC isn't required for us yet" is not the same as "we have no cyber obligations." Because these are class deviations rather than completed rulemaking, expect further movement — verify against acquisition.gov and the DPAP class deviation page.

## Phase-in — verify before citing

The program was designed to phase in over roughly four years, starting with self-assessments and adding third-party certification and Level 3 over time.

**Status as of this skill's last update (August 2026):** On July 13, 2026, DoD/DoW suspended Phase 2 and Phase 3 of the phase-in and stood up a **CMMC Reform Task Force** to review the program, with a stated aim of lowering cost and barriers for small and mid-sized businesses and reconsidering the third-party assessment model. Phase 1 requirements — Level 1 and Level 2 **self**-assessments — remained in force. An RFI closed August 14, 2026, and task force recommendations were expected around mid-September 2026. Instruments reportedly under consideration included a class deviation, a DFARS change, or amendment of 32 CFR Part 170.

**Everything in the preceding paragraph may have been superseded.** Search before advising. The right posture to communicate to clients during this period: the 800-171 obligation under 7012 has not gone anywhere, so security work retains its value regardless of how the certification mechanism is restructured; what is uncertain is the assessment mechanism and its timing, not the underlying control baseline. Clients who stop work during the pause will be behind whenever it resumes.

## Rev 3 adoption — verify before citing

The CMMC Level 2 basis is NIST SP 800-171 **Rev 2**. DoD has signaled a move to Rev 3 through future rulemaking, with an interim final rule discussed for 2026 and industry expectation of a transition no earlier than 2027. Confirm current status before telling a client what they will be assessed against.

## Who assesses what

- **Level 1** — contractor self-assessment, annual, affirmed in SPRS.
- **Level 2 self** — contractor self-assessment where the contract permits, triennial, affirmed annually.
- **Level 2 certification** — a **C3PAO** (CMMC Third-Party Assessment Organization), triennial. Assessors are CCAs; CCPs support preparation.
- **Level 3** — **DCMA DIBCAC**.

**Independence.** A C3PAO cannot both consult on and certify the same client's environment. Redspin operates as a C3PAO, so any advisory conversation that could later become an assessment engagement needs that line respected and named early. If a question sits near it, flag it rather than answering as if it were purely technical.

## Where to check current state

Primary sources, in rough order of authority: the DoD CIO CMMC site (dodcio.defense.gov/CMMC), the Federal Register and eCFR for rule text, DFARS on acquisition.gov, SPRS documentation, and NIST's CSRC for the 800-171/172 publications. Trade press and law firm alerts are useful for spotting that something changed, but confirm the substance against the primary source before putting it in front of a client.
