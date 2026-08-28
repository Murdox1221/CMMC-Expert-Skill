# Assessment Methodology

Source: CMMC Assessment Guide – Level 2, Version 2.13 (dodcio.defense.gov), which implements 32 CFR §§ 170.14(c) and 170.24 and incorporates NIST SP 800-171A. Cite the guide by version; it is revised. The full text of all 110 requirements — statement, objectives, methods and objects, discussion, further discussion, examples, and key references — is bundled at `references/sources/cmmc-assessment-guide-l2-v2.13.md`; search it by requirement ID (e.g. `AC.L2-3.1.1`) rather than reconstructing objective text from memory. Full Part 170 rule text is bundled at `references/sources/32-cfr-part-170.md`.

## How an assessment is actually structured

Each Level 2 requirement in the guide carries a fixed set of elements, and knowing the structure tells a consultant where to look:

- **Requirement number, name, and statement** — `DD.L#-REQ` format (e.g. `AC.L2-3.1.1`). The short name is for quick reference only, not a substitute for the statement.
- **Assessment Objectives [NIST SP 800-171A]** — the lettered determination statements that must all be satisfied.
- **Potential Assessment Methods and Objects [NIST SP 800-171A]** — the examine / interview / test lists.
- **Discussion [NIST SP 800-171 Rev. 2]** — carried over from NIST.
- **Further Discussion** — CMMC-specific expansion, with an Example and Potential Assessment Considerations.
- **Key References**.

The Further Discussion and Potential Assessment Considerations are the CMMC-unique content and the most practically useful part for preparing a client. The objectives and method lists are NIST's, reproduced.

## Assessment objects and methods

**Objects** — what is being assessed. Four kinds:

- **Specifications** — document artifacts: policies, procedures, security plans, functional specifications, architectural designs.
- **Mechanisms** — hardware, software, firmware safeguards.
- **Activities** — protection-related actions involving people (running backups, exercising a plan, monitoring traffic).
- **Individuals** — the people applying the above.

**Methods** — what the assessor does:

- **Examine** — reviewing, inspecting, observing, studying, or analyzing objects, to facilitate understanding, achieve clarification, or obtain evidence.
- **Interview** — discussions with individuals or groups, for the same three purposes.
- **Test** — exercising activities or mechanisms under specified conditions to compare actual against expected behavior.

The guide's own framing of why all three exist is worth repeating to clients almost verbatim: interviews provide information about what staff *believe* to be true, documentation provides evidence of implementing policies and procedures, and testing demonstrates what has or has not actually been done. **The guide states that most objectives will require testing.** A client whose preparation consists of a policy binder is prepared for one method out of three.

**Assessors are not expected to use every method and object listed.** NIST SP 800-171A grants explicit flexibility to determine the level of effort and assurance needed, choosing what is most useful to accomplish the objectives cost-effectively and with sufficient confidence. So the long `[SELECT FROM: …]` lists are a menu, not a checklist — useful for anticipating what *might* be asked, misleading if presented to a client as a required evidence inventory.

## Evidence rules

**Drafts do not count.** Documents must be in final form. Working papers, drafts, and unofficial or unapproved policies are explicitly unacceptable as evidence. This is one of the most common and most avoidable findings — a client with a good policy that was never formally approved fails on that requirement.

Common document types named as potential evidence: policy, process, and procedure documents; training materials; plans and planning documents; and system, network, and data flow diagrams. The guide is clear this list is neither exhaustive nor prescriptive — an organization may not have these specific documents, and others may be reviewed.

For some requirements, observation is the better route: viewing hardware, configuration information, or watching staff follow a process.

Interviews may reach staff at different organizational levels, and they inform not only whether a requirement is implemented but whether **adequate resourcing, training, and planning** exist for people to perform it. That is a broader inquiry than clients expect.

## Findings: MET, NOT MET, NOT APPLICABLE

Defined in 32 CFR § 170.24. A Final Level 2 status (Self or C3PAO) requires MET or N/A on **all** Level 2 requirements.

**MET** — all applicable objectives satisfied based on final-form evidence. Best practice is to record statements conforming to each objective with supporting evidence.

**NOT MET** — one or more objectives not satisfied. In a certification assessment the assessor documents why the evidence does not conform, per objective.

**NOT APPLICABLE** — the requirement or objective does not apply at assessment time; record why. The guide's own example is `SC.L2-3.13.5` (public-access system separation) where no publicly accessible systems exist in scope. **An objective assessed N/A is equivalent to MET for scoring.** And note the asymmetry: a requirement can still be applicable even when some of its objectives are N/A — it is NOT MET only when an *applicable* objective is NOT MET.

**Every objective must yield MET or N/A for the requirement to score MET. One NOT MET objective fails the entire requirement.** Assessments are conducted and captured at the objective level. Assessors exercise judgment on when evidence is sufficient and adequate.

## Three things that count as MET but clients assume don't

These are the highest-value facts in the whole methodology chapter, because they change remediation sequencing and are widely misunderstood. They are stated here as **rules** — what the CFR and the guide say a category of evidence counts as. Explaining the rule to a client ("the rule treats a documented enduring exception as MET") is fine and is exactly what this file is for. Looking at a specific client's specific SSP language and declaring *their* exception MET is the compliance determination `SKILL.md`'s hard rule reserves for a certified assessor — don't cross that line even when the general rule points clearly toward a yes.

**1. Enduring Exceptions are MET.** When an enduring exception is described in the system security plan along with any mitigations, it **shall be assessed as MET** — not NOT MET, not deferred to a POA&M. This matters enormously for manufacturing clients with equipment that cannot support a control. The work is documenting the exception and its mitigations properly in the SSP. Note that the Scoping Guide observes a Specialized Asset may be eligible for an Enduring Exception.

**2. Temporary deficiencies with an operational plan of action are MET.** A temporary deficiency appropriately addressed in an operational plan of action — one that includes deficiency reviews, milestones, and shows progress toward corrections that reduce or eliminate the vulnerability — **shall be assessed as MET**. This is distinct from the formal CMMC POA&M under 32 CFR § 170.21 and is not subject to its eligibility limits or 180-day clock. Do not conflate the two in client advice; they are different instruments with different consequences, and confusing them either wastes remediation budget or creates false comfort.

**3. Requirements satisfied by the enterprise or an ESP are MET.** A requirement is MET if adequate evidence shows the broader enterprise or an External Service Provider implements the objectives. An ESP may be external people, technology, or facilities — cloud service providers, managed service providers, managed security service providers, or cybersecurity-as-a-service providers.

Also: if a client previously received a favorable **DoD CIO adjudication** that a requirement is not applicable or that an alternative measure is equally effective, that adjudication **must be included in the SSP** to be considered. Adjudicated equally-effective measures are assessed as MET provided the environment has not changed. The variance mechanism is at DFARS 252.204-7012(b)(2)(ii)(B)–(C) and is underused.

## Deliverable and reassessment

The primary deliverable is a compliance score and a report containing the findings for each requirement. POA&M closeout assessments evaluate only the NOT MET requirements identified with POA&M items, not the full scope.

Per the Scoping Guide, a **new assessment** is required for significant architectural or boundary changes — network expansions, mergers and acquisitions. Operational changes within an existing scope that follow the existing SSP do not require reassessment and are covered by the annual affirmation.

## How to use this with clients

Preparation advice that follows from the above, in rough priority order: get every policy formally approved and out of draft; expect to demonstrate, not just describe; walk the objectives rather than the requirements; document enduring exceptions and their mitigations in the SSP rather than treating them as gaps; keep operational plans of action current with real milestones; and obtain the customer responsibility matrix from every ESP so inherited requirements can actually be evidenced.

For the authoritative objective text and the per-requirement Further Discussion, Examples, and Potential Assessment Considerations, search `references/sources/cmmc-assessment-guide-l2-v2.13.md` by requirement ID first. Only fall back to fetching the current guide from dodcio.defense.gov if you have reason to think a newer version has been published since v2.13 (September 2024) — check the version number on dodcio.defense.gov if the client's timeline makes that plausible. Do not paraphrase objective text from memory into anything client-facing.
