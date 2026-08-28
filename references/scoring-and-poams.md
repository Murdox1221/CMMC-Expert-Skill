# SPRS Scoring, POA&Ms, and Affirmations

Source: 32 CFR § 170.24 (Scoring Methodology) and § 170.21 (POA&M). Full text bundled at `references/sources/32-cfr-part-170.md` — quote from it directly rather than reconstructing the point-value lists below from memory, in case a future rulemaking changes them.

## The DoD Assessment Methodology

Start at **110**. Subtract for each requirement not fully met:

- **5 points** — requirements whose absence "could lead to significant exploitation of the network, or exfiltration of CUI"
- **3 points** — "specific and confined effect on the security of the network and its data"
- **1 point** — "limited or indirect effect on the security of the network and its data" (the default — everything not named at 5 or 3 points below)

Floor is **−203**; the ceiling is 110. Negative scores are ordinary for organizations that have not started, and a client whose score is −40 is not an outlier.

### The exact point-value list (32 CFR § 170.24(c)(2)(i)(B), Table 7)

Named requirements only — everything else in the 110 is a 1-point item by default.

**5-point requirements (42 total):**
- Basic (23): `AC.L2-3.1.1, AC.L2-3.1.2, AT.L2-3.2.1, AT.L2-3.2.2, AU.L2-3.3.1, CM.L2-3.4.1, CM.L2-3.4.2, IA.L2-3.5.1, IA.L2-3.5.2, IR.L2-3.6.1, IR.L2-3.6.2, MA.L2-3.7.2, MP.L2-3.8.3, PS.L2-3.9.2, PE.L2-3.10.1, PE.L2-3.10.2, CA.L2-3.12.1, CA.L2-3.12.3, SC.L2-3.13.1, SC.L2-3.13.2, SI.L2-3.14.1, SI.L2-3.14.2, SI.L2-3.14.3`
- Derived (19): `AC.L2-3.1.12, AC.L2-3.1.13, AC.L2-3.1.16, AC.L2-3.1.17, AC.L2-3.1.18, AU.L2-3.3.5, CM.L2-3.4.5, CM.L2-3.4.6, CM.L2-3.4.7, CM.L2-3.4.8, IA.L2-3.5.10, MA.L2-3.7.5, MP.L2-3.8.7, RA.L2-3.11.2, SC.L2-3.13.5, SC.L2-3.13.6, SC.L2-3.13.15, SI.L2-3.14.4, SI.L2-3.14.6`

**3-point requirements (14 total):**
- Basic (7): `AU.L2-3.3.2, MA.L2-3.7.1, MP.L2-3.8.1, MP.L2-3.8.2, PS.L2-3.9.1, RA.L2-3.11.1, CA.L2-3.12.2`
- Derived (7): `AC.L2-3.1.5, AC.L2-3.1.19, MA.L2-3.7.4, MP.L2-3.8.8, SC.L2-3.13.8, SI.L2-3.14.5, SI.L2-3.14.7`

**Variable (the two partial-credit requirements — not fixed-value):**
- `IA.L2-3.5.3` (MFA) — **3 points** subtracted if MFA is implemented for remote and privileged users only; **5 points** if not implemented for any users.
- `SC.L2-3.13.11` (FIPS-validated cryptography) — **3 points** subtracted if encryption is employed but not FIPS-validated; **5 points** if encryption is not employed at all.

**Everything else (the remaining ~52 requirements)** is 1 point.

This list is worth having verbatim when a client hands over a gap assessment: you can tell them exactly which items are driving their score, not just which category.

Read the score as a gap map, not a grade. A score of 100 with the two missing requirements both worth 5 points is a worse position than 88 spread across twelve 1-point items, because the 5-pointers are usually architectural and the 1-pointers are usually paperwork. When a client asks "is our score good," the honest answer describes *which* requirements are missing.

Scores are submitted to **SPRS** (Supplier Performance Risk System) and are visible to contracting officers. Note that the clause landscape here changed in February 2026 — see `program-status.md` before citing DFARS 252.204-7019 or -7020, which no longer exist in that form.

## POA&M rules (32 CFR § 170.21)

The rules are much narrower than clients expect, and this is one of the most consequential things to get right in an advisory conversation.

- **Only 1-point requirements** may go on a POA&M. Nothing worth 3 or 5 points is eligible.
- **One exception:** `SC.L2-3.13.11` (CUI encryption) may be POA&M'd if encryption is employed but is not FIPS-validated. Encryption absent entirely is not eligible.
- **Six requirements are barred outright**, regardless of point value: `AC.L2-3.1.20` (external connections), `AC.L2-3.1.22` (control public information), `CA.L2-3.12.4` (system security plan), and `PE.L2-3.10.3`, `PE.L2-3.10.4`, `PE.L2-3.10.5` (physical access to visitors, devices, and control). The SSP one catches people — an incomplete SSP blocks Conditional status entirely. Per § 170.24(c)(2)(i)(B)(5), OSAs must have an SSP in place *at the time of assessment*; its absence produces a specific documented finding — "an assessment could not be completed due to incomplete information and noncompliance with 48 CFR 252.204-7012" — not merely a NOT MET on 3.12.4.
- **Level 3 has its own barred list**, separate from Level 2's: `IR.L3-3.6.1e` (SOC), `IR.L3-3.6.2e` (cyber incident response team), `RA.L3-3.11.1e` (threat-informed risk assessment), `RA.L3-3.11.4e` (security solution rationale), `RA.L3-3.11.6e` (supply chain risk response), `RA.L3-3.11.7e` (supply chain risk plan), `SI.L3-3.14.3e` (specialized asset security). Level 3 also uses the same ≥0.8 score-ratio gate as Level 2, but every Level 3 requirement is worth exactly 1 point (§ 170.24(c)(3)) — there is no 5/3/1 weighting at Level 3.
- **Minimum score to qualify for Conditional status:** the assessment score divided by 110 must be **≥ 0.8** — that is, 88 or higher for Level 2.
- **Every** NOT MET requirement goes on the POA&M, and every one must be eligible. This is the trap in real gap assessments: a score of 92 is 18 points short, and if even one of those points sits on a 3-pointer or a barred requirement, there is no Conditional status at any score. Reconcile the full findings list against eligibility before telling a client the POA&M path is open.
- **180 days** from the Conditional CMMC Status Date to close the POA&M, confirmed by a closeout assessment. Miss it and the Conditional status expires; there is no extension mechanism.
- **No POA&Ms at Level 1.** Level 1 self-assessment is all-or-nothing.

Practical consequence worth stating plainly to clients: the POA&M is not a financing mechanism for the expensive work. The requirements clients most want to defer — FIPS encryption, MFA, boundary protection, audit — are precisely the 3- and 5-point items that cannot be deferred. Plan for them before assessment, not after.

## Conditional vs Final status

**Conditional** means the assessment passed at ≥80% with an eligible POA&M outstanding. **Final** means all requirements are MET. Both are recorded, both are visible, and the distinction matters for contract eligibility and for Level 3 prerequisites. A Conditional status that expires does not degrade to something lesser — it expires, and the organization is uncertified.

## Affirmations

A **Senior Official** of the contractor affirms continuing compliance in SPRS at initial assessment, annually thereafter, and at POA&M closeout. This person must be an employee of the organization with authority to make the representation.

Treat this with weight in any advisory conversation. An affirmation is a representation to the Government about the state of a system, made in support of contract eligibility, and the False Claims Act consequences of an inaccurate one are real and have been litigated. When a client asks whether they can affirm while something is still in flight, the answer is not a technical answer — route them to counsel. Note that you are an AI assistant and this needs qualified legal review before it becomes a position.

## Scope of a score

A score and a CMMC status attach to a **defined scope**, not to a company. An organization can hold a Final Level 2 status for an enclave and have the rest of its network entirely out of scope. When a client reports "we're certified," the first clarifying question is always: certified for what boundary, and does the work under this contract happen inside it?
