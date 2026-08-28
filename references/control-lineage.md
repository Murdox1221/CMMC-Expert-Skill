# Control Lineage: SP 800-53 → SP 800-171

## Why this matters

SP 800-171 requirements are compressed. They were written as short, outcome-style statements derived from longer SP 800-53 controls, and the compression stripped out the reasoning. When a requirement says "periodically," "as needed," or "limit system access to authorized users," the text alone does not tell you what an assessor will expect — but the parent SP 800-53 control, with its supplemental guidance or discussion, usually does.

So whenever the question is what a requirement *means* or *requires* — not only when it looks ambiguous — the move is: **find the parent control, read its Discussion, and reason from the intent.** That is not freelancing. NIST built 800-171 by tailoring 800-53, published the mapping, and the discussion text is the closest thing to an official statement of what the requirement is trying to accomplish.

**This is bundled — use it, don't recall it. Two tracks:**

**Default — SP 800-171 Rev 2 → SP 800-53 Rev 4** (the CMMC Level 2 basis):

- `references/sources/sp-800-171r2-to-800-53r4-mapping.md` — SP 800-171 Rev 2 Appendix D (Tables D-1–D-14), the parent SP 800-53 Rev 4 control(s) for each of the 110 requirements. Look the requirement up here first.
- `references/sources/sp-800-53-rev4-cui-parents.md` — verbatim *Control* text and *Supplemental Guidance* for every one of those parent controls (SP 800-53 Rev 4, from NIST's OSCAL catalog). Quote from here first; cite as "<ID>, SP 800-53 Rev 4."

**Secondary lens — SP 800-171 Rev 3 → SP 800-53 Rev 5.** Rev 3 restated the same requirement families against the current catalog, and Rev 5's *Discussion* is frequently fuller and clearer than Rev 4's *Supplemental Guidance* on the identical control. Use it to sharpen an interpretation, not to replace the default:

- `references/sources/sp-800-171r3-to-800-53r5-mapping.md` — Rev 3 `03.xx.xx` (≈ Rev 2 `3.x.x`) → SP 800-53 Rev 5 parents. 33 Rev 2 requirements were consolidated in Rev 3 and have no direct row; for those, stay on the Rev 4 default.
- `references/sources/sp-800-53-rev5-cui-parents.md` — verbatim *Control* text and *Discussion* for every Rev 5 parent under either mapping (~171). Cite as "SP 800-53 Rev 5" and say you are reading through the Rev 3 lens.

For a control in neither set (Level 3 / 800-172 lineage, or a related control named inside a Discussion), fetch it from the NIST CPRT catalog (`csrc.nist.gov/projects/cprt`) or `csrc.nist.gov`, and say you did.

An interpretive answer that never names or quotes the parent 800-53 control is incomplete. Lead with Rev 4; never silently blend the two catalogs — name the revision each quote came from.

Two disciplines keep this honest:

- **The 800-171 requirement is what gets assessed**, not the 800-53 control. Use the parent control to interpret intent, never to import obligations the requirement did not carry over. An assessor grades against SP 800-171A objectives. If you tell a client they must do something because 800-53 says so, and 800-171 doesn't, you have invented a requirement.
- **Mind the revision seam.** SP 800-171 Rev 2's Appendix D maps to SP 800-53 **Rev 4**; SP 800-171 Rev 3 maps to **Rev 5**. Base-control identifiers and intent are stable across Rev 4→Rev 5, but Rev 5 rewrote statements to be outcome-based, moved baselines to SP 800-53B, and renumbered/withdrew/merged several enhancements (seven that Rev 2 cites are flagged WITHDRAWN in the Rev 5 parent-text file, with their successor). The Rev 3 mapping is machine-derived from NIST's Rev 3 OSCAL, not a published crosswalk — reliable for *finding the control to interpret from*, not a compliance crosswalk.

## The derivation, by revision

| | SP 800-171 Rev 2 | SP 800-171 Rev 3 |
|---|---|---|
| Published | Feb 2020 (updates through Jan 28, 2021) | May 14, 2024 |
| Parent catalog | **SP 800-53 Rev 4** | **SP 800-53 Rev 5** |
| Starting point | FIPS 200 + the moderate baseline | The moderate baseline, via SP 800-53B |
| Requirements | 110 in 14 families | 97 in 17 families |
| Assessment companion | SP 800-171A | SP 800-171A Rev 3 |
| Where the mapping lives | Appendix D (mapping tables) and Appendix E (tailoring criteria) | The **CUI Overlay** spreadsheet published with Rev 3 on CSRC |
| Status at NIST | **Withdrawn May 14, 2024** | Current |

**The Rev 2 withdrawal is a live oddity worth understanding.** NIST withdrew Rev 2 when Rev 3 published, but the CMMC Program rule at 32 CFR Part 170 identifies Level 2 requirements as those of Rev 2. So CMMC Level 2 is currently assessed against a NIST publication that NIST itself has withdrawn. That is a regulatory-pointer question, not a NIST question, and it resolves when DoD completes rulemaking. Note also that DFARS 252.204-7012(b)(2)(i) points to NIST SP 800-171 "in effect at the time the solicitation is issued or as authorized by the Contracting Officer" — a moving pointer that can diverge from what the CMMC rule specifies. When a client asks which revision applies, the answer depends on which instrument you are reading, and saying so is more accurate than picking one.

## Rev 2's tailoring criteria (Appendix E)

NIST started from the SP 800-53 Rev 4 moderate baseline and sorted every control into one of four buckets. Understanding these explains most "why isn't X in 800-171?" questions:

- **CUI** — directly relates to protecting CUI confidentiality. These became the 110 requirements.
- **NFO** — expected to be routinely satisfied by nonfederal organizations without being specified. Tailored out of the requirement list, but NIST's stated expectation is that they are being done. Policy and procedure controls live here.
- **FED** — primarily the federal government's responsibility. Tailored out.
- **NCO** — not directly related to protecting CUI confidentiality. Tailored out.

**The single most useful consequence: SP 800-171 protects confidentiality only.** Availability and integrity controls were tailored out as NCO. The contingency planning family is the clean illustration, and it repays precision:

- There is **no requirement to make backups** in 800-171. CP-9 (system backup) was tailored out.
- There **is** a requirement to protect the confidentiality of backups that exist — `MP.L2-3.8.9`, "protect the confidentiality of backup CUI at storage locations," worth 1 point. Rev 3 keeps the same posture at 03.08.09.

So NIST took the confidentiality half of the backup control and left the availability half behind — twice, deliberately, across two revisions. That is a much stronger answer to a client than "backups aren't required," and it is precise enough to survive challenge: the honest phrasing is that 800-171 governs how backups must be protected, not whether they must be taken.

Say the rest too. DFARS 252.204-7012(e) requires preserving images and monitoring data for 90 days after an incident report — which can collide with a restore-immediately instinct. Ransomware is the DIB's most common real-world event, and a client with no backups is one bad morning from losing the business. Note also the scoping consequence: a new backup platform holding CUI pulls 3.8.9, media protection, and encryption requirements along with it, and if it is a hosted service it may drag ESP obligations in too. The requirement to *have* backups is absent; the advice is not, and neither is the scoping impact once they exist.

The NFO bucket is the other one clients trip on. A client who has never written a policy is not compliant merely because policy controls were tailored out — SP 800-171A objectives frequently require documented, defined, or specified elements, which is the tailored-out policy expectation reappearing at assessment time.

## What changed in SP 800-53 Rev 5, and why it matters for Rev 3

Rev 5 (September 2020) was a structural rewrite, not a content refresh:

- **Outcome-based control statements.** Rev 4 said "the information system shall…" or "the organization shall…"; Rev 5 removed the actor and states the outcome. This is why Rev 3's requirements read differently even where the substance is unchanged.
- **Baselines separated out.** Rev 4 carried low/moderate/high baselines inside the document. Rev 5 moved them to **SP 800-53B**. Cite 800-53B, not 800-53, when the point is about baselines.
- **"Supplemental Guidance" became "Discussion."** Same interpretive role, different heading — worth knowing so you cite the right thing.
- **Two new families:** **PT** (Personally Identifiable Information Processing and Transparency) and **SR** (Supply Chain Risk Management), taking the catalog from 18 families to 20, with privacy controls integrated rather than kept in a separate appendix.
- **CA renamed** to Assessment, Authorization, and Monitoring — which is why Rev 3's CA family carries that name rather than Rev 2's "Security Assessment."

Rev 3's three added families — **PL** (Planning), **SA** (System and Services Acquisition), **SR** (Supply Chain Risk Management) — largely reflect NFO expectations from Rev 2 being made explicit, plus Rev 5's supply chain emphasis. The full Rev 3 family list, per NIST: AC, AT, AU, CA, CM, IA, IR, MA, MP, PE, PL, PS, RA, SA, SC, SI, SR.

**Organization-defined parameters (ODPs)** are Rev 3's most consequential change for assessment practice. Rev 5 controls contain assignment and selection operations — bracketed values the implementing organization fills in. Rev 2 hard-coded many of these or left them vague ("periodically"); Rev 3 exposes them as explicit ODPs, some of which the federal agency specifies and some of which the contractor does. The practical effect is that a contractor must now *state* its parameter values and defend them, and an assessor evaluates against the stated value. Ambiguity moves from the standard into the SSP, which is better for rigor and harder for unprepared clients.

## Worked examples

These illustrate the method. Confirm the exact mapping in Appendix D (Rev 2) or the CUI Overlay (Rev 3) before relying on a specific pairing.

**"Periodically" and other undefined frequencies.** Rev 2 uses vague cadence language throughout. The parent Rev 4 control almost always contains an `[Assignment: organization-defined frequency]` where 800-171 wrote "periodically." That tells you NIST's intent was never a fixed interval — it was that the organization define one and follow it. So the defensible client answer is: pick a frequency, document it in the SSP, and hold to it. An assessor's finding will be the absence of a defined and followed frequency, not the wrong number. Rev 3 makes this explicit as an ODP.

**This is no longer just an inference — the CMMC rule itself puts a number on it.** 32 CFR § 170.14(d) states that within CMMC, "organization-defined" means as determined by the OSA (except where it refers to an actual Level 3 ODP), and "periodically means occurring at regular intervals," adding: "the interval length is organization-defined to provide contractor flexibility, **with an interval length of no more than one year**." That ceiling is regulatory text, not a consultant's rule of thumb — cite § 170.14(d) directly when a client wants a hard number for a "periodically" requirement and doesn't want to argue for a shorter cadence than the assessor might otherwise expect. It does not tell them the *right* interval (that's still their call, and shorter is often warranted, e.g. daily log review), only the outer bound CMMC will accept.

**AC.L2-3.1.1 (limit system access to authorized users, processes, and devices).** Maps to the Rev 4 account management and access enforcement controls. The requirement reads as a one-line statement about access; the parent controls describe an account lifecycle — creation, modification, review, disabling on termination. That lifecycle is where SP 800-171A objectives and assessor interviews go, and it is why "we have Active Directory" never satisfies this requirement.

**AU.L2-3.3.1 (create and retain audit logs).** The parent audit controls explain that event selection is supposed to be a reasoned decision tied to what the organization needs to investigate, and that logs exist to support after-the-fact reconstruction. That is the answer to a client asking "which events do we have to log?" — there is no universal list, there is a documented rationale, and NIST's own discussion suggests deriving the event list from the organization's other security requirements. Note that Rev 3 *still* declines to set a retention number, pointing instead at the organization's records retention policy: two revisions of deliberate silence is strong evidence the omission is intent, not oversight. The 800-171A objectives resolve what is actually graded — that event types are specified, that a retention period is defined, and that it is followed. A consultant can recommend a specific figure as advice, but should label it as advice rather than as a requirement, and should not present a FedRAMP or other baseline parameter as if it bound the client.

**CM.L2-3.4.1 (baseline configurations and inventories).** The parent configuration management controls define what a baseline configuration actually is — a documented, formally reviewed set of specifications serving as a known-good reference. Clients routinely present a hardening script and think they are done; the parent control shows the expectation is a maintained, versioned artifact.

**SC.L2-3.13.11 (FIPS-validated cryptography).** The parent cryptographic control clarifies that the point is validated implementation, not merely strong algorithms. This is the interpretive basis for telling a client that BitLocker enabled without FIPS mode does not meet the requirement — and it is the requirement with the narrow POA&M carve-out under 32 CFR § 170.21, so getting the interpretation right has direct consequences.

## SP 800-172 and Level 3

SP 800-172 provides enhanced security requirements for CUI facing advanced persistent threats, layered on top of 800-171 and drawn from the 800-53 catalog. Note that **SP 800-172 Rev 3 and SP 800-172A Rev 3 now exist**, so the same regulatory-pointer question applies as with 800-171: confirm which revision the CMMC rule and the contract actually invoke before advising. CMMC Level 3 uses a selected subset — 24 requirements — not the full publication.

## Authoritative sources

Use these, not vendor summaries: `csrc.nist.gov` and `nvlpubs.nist.gov` for the 800-53, 800-53B, 800-171, 800-171A, 800-172 and 800-172A publications and their supplemental spreadsheets (the Rev 2→Rev 3 change analysis and the CUI Overlay are both published there); the NIST CPRT catalog for structured control data; `ecfr.gov` for 32 CFR Part 170; `acquisition.gov` for DFARS clause text. The full text of 32 CFR Part 170 and the Assessment Guide's per-requirement discussion are bundled at `references/sources/32-cfr-part-170.md` and `references/sources/cmmc-assessment-guide-l2-v2.13.md` for direct quoting. The lineage material is bundled: `references/sources/sp-800-171r2-to-800-53r4-mapping.md` + `references/sources/sp-800-53-rev4-cui-parents.md` (default: Rev 2 → Rev 4, *Control* + *Supplemental Guidance*), and `references/sources/sp-800-171r3-to-800-53r5-mapping.md` + `references/sources/sp-800-53-rev5-cui-parents.md` (secondary lens: Rev 3 → Rev 5, *Control* + *Discussion*). Quote the parent guidance from there rather than paraphrasing it, and name the revision.
