# Levels, Controls, and Assessment Objectives

Full text of the CMMC Program rule (levels, numbering scheme, Level 3's selected requirement table) is bundled at `references/sources/32-cfr-part-170.md`, § 170.14. Full per-requirement objectives for all 110 Level 2 requirements are at `references/sources/cmmc-assessment-guide-l2-v2.13.md`.

## The three levels

| | Level 1 | Level 2 | Level 3 |
|---|---|---|---|
| Protects | FCI | CUI | CUI on programs facing advanced persistent threats |
| Source | FAR 52.204-21 | NIST SP 800-171 Rev 2 | Level 2 + NIST SP 800-172 subset |
| Count | 15 requirements | 110 requirements | 24 additional requirements |
| Assessed by | Self | Self **or** C3PAO, depending on the contract | DCMA DIBCAC |
| Cadence | Annual self-assessment | Triennial assessment, annual affirmation | Triennial, annual affirmation |
| POA&M allowed | No | Yes, narrowly (see scoring reference) | Yes, narrowly |

Level 3 requires a **Final** Level 2 certification for the same scope first. A conditional Level 2 does not qualify.

**FCI vs CUI** is the fork that determines everything downstream. FCI is information provided by or generated for the Government under a contract that is not intended for public release — essentially any non-public contract information. CUI is a formal designation under 32 CFR Part 2002 with categories in the NARA CUI Registry; in the defense space it is most often Controlled Technical Information (CTI) or Export Controlled. Every organization holding CUI also holds FCI. Many small subcontractors that believe they hold CUI actually only hold FCI, and the reverse mistake is also common — a distribution statement B through F on a drawing is a strong CTI indicator. When a client is unsure, the contract, the DD Form 254, and the markings on delivered data are where the answer lives, not the client's intuition. For the designation authority, the Basic/Specified distinction, marking obligations, and what to do when the government sends unmarked data, see `cui-program.md` — those questions come up constantly and CMMC does not answer them.

## Rev 2 families (current CMMC Level 2 basis)

Fourteen families, 110 requirements:

AC (Access Control, 22) · AT (Awareness and Training, 3) · AU (Audit and Accountability, 9) · CM (Configuration Management, 9) · IA (Identification and Authentication, 11) · IR (Incident Response, 3) · MA (Maintenance, 6) · MP (Media Protection, 9) · PS (Personnel Security, 2) · PE (Physical Protection, 6) · RA (Risk Assessment, 3) · CA (Security Assessment, 4) · SC (System and Communications Protection, 16) · SI (System and Information Integrity, 7)

CMMC requirement identifiers map to the 800-171 numbering: `AC.L2-3.1.1` is family AC, Level 2, 800-171 requirement 3.1.1. Level 1 identifiers use `L1` and map to FAR 52.204-21 basic safeguards, which are a subset of the 800-171 controls.

## Rev 3 (not yet the CMMC basis — verify before advising)

NIST published SP 800-171 Rev 3 on May 14, 2024: **97 requirements across 17 families** — AC, AT, AU, CA, CM, IA, IR, MA, MP, PE, PL, PS, RA, SA, SC, SI, SR — adding Planning (PL), System and Services Acquisition (SA), and Supply Chain Risk Management (SR). It reorganizes rather than simply reduces; the drop from 110 to 97 comes from consolidation, and Rev 3 introduces organization-defined parameters (ODPs), which shift real interpretive work onto the contractor and the assessor. See `control-lineage.md` for how Rev 3 derives from SP 800-53 Rev 5 and what ODPs change about assessment.

**Rev 2 was withdrawn by NIST on the day Rev 3 published.** The CMMC Program rule nonetheless identifies Level 2 requirements as Rev 2's, so Level 2 is currently assessed against a withdrawn publication — a regulatory-pointer artifact, not a NIST position. Note too that DFARS 252.204-7012(b)(2)(i) invokes 800-171 "in effect at the time the solicitation is issued," which can point somewhere different from the CMMC rule. **Search for current status before telling a client which revision they will be assessed against**, and be precise about which instrument you are answering from. The practical advice — build to Rev 2, watch Rev 3, don't rearchitect yet — depends on where that rulemaking actually stands.

## Assessment objectives are where assessments are won and lost

NIST SP 800-171A decomposes the 110 requirements into roughly 320 discrete assessment objectives, lettered a, b, c… Each is scored MET, NOT MET, or NOT APPLICABLE, and a single NOT MET objective makes the whole requirement NOT MET. There is no partial credit at the requirement level.

This is the most common gap between how clients think about compliance and how they are actually assessed. A client says "we do access control" and means they have Active Directory; the objectives ask separately whether authorized users are *defined*, whether transactions and functions are *defined*, and whether the system *limits* access to each. Policy without evidence of operation fails. Evidence without policy fails.

For Level 3, NIST SP 800-172A does the same decomposition for the enhanced requirements.

Assessors draw on three evidence types — **examine** (documents, configs), **interview** (people describing what they do), and **test** (observing the control operate). Advice that produces only documents will not survive a certification assessment.

## Level 3 enhanced requirements

The 24 selected 800-172 requirements target advanced persistent threats and assume the Level 2 baseline is already operating. Note that SP 800-172 Rev 3 and SP 800-172A Rev 3 now exist, so the same revision-pointer question applies as with 800-171 — confirm which revision the CMMC rule and the contract actually invoke. They lean toward threat hunting, dual authorization, penetration-resistant architecture, and supply chain risk. They are assessed by DIBCAC, not a C3PAO. Very few organizations are in scope; if a client believes they need Level 3, confirm it against the actual contract requirement before scoping work — it is far more often assumed than required.
