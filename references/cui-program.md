# The CUI Program: 32 CFR Part 2002 and the DoD CUI Program

CMMC is a verification mechanism bolted onto an information-handling program that existed first and governs independently. Consultants who know only CMMC keep hitting questions they cannot answer — why the government won't say what's CUI, why one category carries extra handling rules, why an unmarked drawing is still a problem. Those answers live here, in 32 CFR Part 2002 and DoDI 5200.48.

**Bundled primary sources.** Full text of Executive Order 13556 and 32 CFR Part 2002 are at `references/sources/eo-13556.md` and `references/sources/32-cfr-part-2002.md` (both current as of the August 25, 2026 eCFR/Federal Register snapshot — no amendments found in either since original publication). Quote from these directly rather than reconstructing regulatory text from memory. **DoDI 5200.48 and DoDI 5230.24 are not currently bundled** — they could not be fetched programmatically (esd.whs.mil and its mirrors return 403 to automated requests) — so for exact text from either, fetch live from `esd.whs.mil` (search "DoDI 5200.48" / "DoDI 5230.24") or ask the user if they can supply the PDFs directly, the way the CMMC guides and Part 170 were supplied.

## Governance chain

**Executive Order 13556** (November 4, 2010), Sec. 2(c): "The National Archives and Records Administration shall serve as the Executive Agent to implement this order and oversee agency actions to ensure compliance with this order." This established a government-wide CUI Program to replace the sprawl of agency-invented markings — FOUO, SBU, LES and dozens more. **NARA delegated that authority to the Director of the Information Security Oversight Office (ISOO)** (32 CFR § 2002.4(m)).

**32 CFR Part 2002** is the implementing regulation. It binds executive branch agencies. Critically, **§ 2002.1(f)**: *"This part applies to all executive branch agencies that designate or handle information that meets the standards for CUI. This part does not apply directly to non-executive branch entities, but it does apply indirectly to non-executive branch CUI recipients, through incorporation into agreements."* (Note the correct citation is § 2002.1(f) — the "Purpose and scope" section — not § 2002.3, which doesn't exist in this part; § 2002.2 is followed by § 2002.4.) That sentence is the whole architecture. A contractor is not regulated by Part 2002; a contractor is bound by whatever the contract says, and the contract is supposed to carry Part 2002's requirements forward.

**The CUI Registry** (archives.gov/cui) is the authoritative list of categories and subcategories, their authorizing laws, their markings, and whether each is Basic or Specified. If a category is not in the Registry, it is not CUI.

**DoDI 5200.48, "Controlled Unclassified Information (CUI)"** (effective March 6, 2020) implements the program inside DoD — identification, marking, safeguarding, dissemination, destruction, and records management. DoD maintains a **DoD CUI Registry** that mirrors the national Registry while adding DoD-specific indexes and relationships. When a DoD question and a NARA answer seem to conflict, check the DoD issuance; when they agree, cite the CFR.

## CUI Basic vs CUI Specified

This is the distinction most consultants skip, and it changes what a client must actually do.

**CUI Basic** (§ 2002.4(j)) — the authorizing law, regulation, or government-wide policy requires or permits protection but *does not specify how*. Handled under the uniform controls in Part 2002 and the Registry. This is the default: § 2002.14(b)(1) makes CUI Basic the standard applied to all CUI unless the Registry annotates it as Specified.

**CUI Specified** — the authority *does* prescribe specific handling or dissemination controls. Authorized holders follow the underlying authority's requirements (§ 2002.14(b)(2)(i)). Where that authority is silent on some aspect, CUI Basic standards fill the gap — unless doing so would conflict with the Specified authority, in which case the Specified standard governs (§ 2002.14(b)(2)(ii)).

Operationally: a client handling Export Controlled CUI is not just handling "CUI." The underlying ITAR/EAR obligations — U.S. persons access, licensing, deemed export — ride along and are not satisfied by implementing 800-171. This is why "we're CMMC Level 2 compliant" and "we're handling this data lawfully" are different claims. Check the Registry entry for every category a client actually holds; the safeguarding answer can differ per category.

**Do not assume the defense categories are Basic.** Per the CUI Registry, **Controlled Technical Information is CUI Specified** — banner marking `CUI//SP-CTI`, with its safeguarding and dissemination authority listed as 48 CFR 252.204-7012. So the most common category in the DIB is Specified, and the clause a consultant already knows is the very authority that makes it so. Verify each category in the Registry rather than defaulting to Basic; the assumption runs the wrong way from what most people expect.

## The safeguarding standard, and the line that decides which standard applies

**§ 2002.14(g):** CUI Basic is categorized at **no less than the moderate confidentiality impact level** per FIPS 199. Agencies apply FIPS 200 and SP 800-53 controls per their risk-based tailoring. Agencies may raise CUI Basic above moderate only internally or by agreement — they may not unilaterally impose higher-than-moderate controls when disseminating CUI Basic outside the agency.

**§ 2002.14(h) draws the line that governs everything downstream:**

- A **Federal information system** is one used or operated by an agency, *or by a contractor or other organization on behalf of an agency*. Systems a non-executive-branch entity operates on behalf of an agency "are subject to the requirements of this part as though they are the agency's systems." That means the full FIPS 200 / SP 800-53 regime — not 800-171.
- A **non-Federal information system** is anything else. Here the regulation states that **NIST SP 800-171 defines the requirements necessary to protect CUI Basic**, and agencies **must** use 800-171 when establishing security requirements for CUI confidentiality on non-Federal systems — unless the Registry authority for that category prescribes specific safeguarding requirements, or an agreement establishes protection above moderate.

**This is a frequently-missed scoping trap.** A contractor operating a system *on behalf of* the government is in the 800-53 world, not the 800-171 world, and CMMC is not the applicable yardstick. The regulation clarifies the boundary: when a non-executive-branch entity "receives Federal information only incidental to providing a service or product to the Government other than processing services, its information systems are not considered Federal information systems." DFARS 252.204-7012(b)(1) mirrors this split — systems operated on behalf of the Government follow requirements specified elsewhere in the contract, with cloud services routed to DFARS 252.239-7010. If a client's environment might be operating on behalf of the government, resolve that before scoping anything else.

Part 2002 also addresses **destruction** (§ 2002.14(f) — unreadable, indecipherable, irrecoverable; SP 800-88 methods), **reproduction** (§ 2002.14(e) — equipment must not retain data), **controlled environments** (§ 2002.14(c)), and **shipping** (§ 2002.14(d)).

## Agreements: how obligations actually reach a contractor

§ 2002.16(a)(5) — agencies **should** enter formal information-sharing agreements with non-executive-branch entities they share CUI with, "whenever feasible." § 2002.16(a)(6) sets the floor for what such an agreement must contain at minimum: that the entity handles CUI in accordance with the Order, Part 2002, and the Registry; that misuse carries penalties under applicable law; and that the entity reports non-compliance back to the disseminating agency. § 2002.16(a)(5)(ii) covers the no-agreement case — where a formal agreement isn't feasible but the agency's mission still requires disseminating CUI, the agency must at least communicate to the recipient that the government strongly encourages protection consistent with the Order, Part 2002, and the Registry.

Note the word "should." The regulation does not force a clause into every instrument, which is a large part of why CUI flowdown in practice is inconsistent. It is also why **FAR Case 2017-016** matters: a proposed FAR CUI rule was published January 15, 2025 (90 FR 4278), proposing a standard form to communicate CUI requirements uniformly across agencies and contracts. **Confirm its current status before advising** — as of mid-2026 it had not been finalized, and it sits inside a broader FAR overhaul that has been reshuffling acquisition regulations.

Other sections worth knowing: § 2002.12 (categories and subcategories), § 2002.18 (decontrolling), § 2002.20 (marking), § 2002.36 (legacy materials), § 2002.38 (waivers), § 2002.54 (misuse of CUI).

## Marking, and the unmarked-CUI problem

Part 2002 requires CUI to be marked uniformly and conspicuously per the Registry (§ 2002.20). The full mechanics — banner markings, the designation indicator identifying the designating agency and point of contact, portion marking, category markings, and limited dissemination control markings — are elaborated in the CUI Marking Handbook published by the Executive Agent. Limited dissemination controls (LDCs) must align with those the Executive Agent established under § 2002.16(b)(4); agencies cannot invent their own.

**In DoD practice, the government frequently fails to mark.** DoDI 5200.48 places the identification and marking obligation on the government as the designating authority, and DFARS 252.204-7012's definition of covered defense information includes information "marked or otherwise identified in the contract" — but real drawings arrive unmarked, or arrive marked only with a legacy distribution statement, all the time.

This is genuinely hard advice, so give it carefully. What is defensible: the contractor is not the CUI designating authority and cannot unilaterally decide the government's data is or isn't CUI. The right first move is to ask the contracting officer for a written determination — that creates a record and shifts the question to the party that owns it. In the meantime, the prudent posture is to protect the data as if it were CUI, because the cost of over-protecting is operational friction while the cost of under-protecting is a reportable incident and potential contract exposure. Note that the 7012 definition's second prong reaches information "collected, developed, received, transmitted, used, or stored by or on behalf of the contractor in support of the performance of the contract" — which sweeps in contractor-generated derivative material, not just what the government handed over. Do not tell a client that unmarked means unprotected.

## Controlled Technical Information and distribution statements

DFARS 252.204-7012 defines **controlled technical information** as technical information with military or space application subject to controls on access, use, reproduction, modification, performance, display, release, disclosure, or dissemination — information that would meet the criteria for **distribution statements B through F** under **DoDI 5230.24, Distribution Statements on Technical Documents**. It excludes information lawfully publicly available without restrictions.

The CUI Registry entry for CTI goes further than "indicator": it states that controlled technical information **is to be marked with one of the distribution statements B through F** in accordance with DoDI 5230.24, and it names engineering drawings, specifications, standards, process sheets, manuals, and technical reports among the examples.

The practical read: **a distribution statement B through F on an engineering drawing is the government's own marking that the document is CTI**, and CTI is CUI Specified. Distribution statement A means approved for public release — not CTI. This is the single most useful field test to teach a client's engineering staff, because it uses a marking they already see on drawings. It also means the absence of a `CUI//SP-CTI` banner on a drawing carrying Statement C is a marking defect on the government's side, not evidence that the data is uncontrolled.

**Covered defense information** under 7012 is the broader term: unclassified CTI *or other information described in the CUI Registry* that requires safeguarding or dissemination controls and is either (1) marked or otherwise identified in the contract and provided to the contractor by or on behalf of DoD, or (2) collected, developed, received, transmitted, used, or stored by or on behalf of the contractor in support of contract performance. CDI and CUI are not perfectly synonymous, and in a careful written answer it is worth using the term the governing instrument uses.

## How this connects to CMMC

The division of labor is the point:

- **The government decides what is CUI.** It is the designating authority, it marks, and it specifies requirements in the contract. 32 CFR Part 2002 and DoDI 5200.48 govern that side.
- **The contractor decides how to protect it**, within the requirements the contract carries — SP 800-171 for non-Federal systems, per § 2002.14(h) and DFARS 252.204-7012(b)(2).
- **CMMC verifies that the contractor did what it said**, at the level the contract specifies, under 32 CFR Part 170 and the DFARS CMMC clauses.

Two consequences worth stating to clients:

**Identification precedes protection, and clients skip it.** Organizations buy tooling and enclaves before establishing what CUI they actually receive, in what form, and under which Registry categories. Scoping is impossible without that inventory, and the answer often shrinks the problem — many suppliers that assume they hold CUI hold only FCI.

**CMMC compliance is not CUI Program compliance.** A client can hold a Final Level 2 status and still mishandle CUI — mismarking, over-disseminating, failing Specified-category obligations like export control, destroying records improperly. 800-171 addresses confidentiality on information systems. The CUI Program addresses the whole lifecycle including paper, conversations, marking, dissemination, and decontrol. When a client asks "are we good on CUI," CMMC status answers part of the question and it is worth naming the part it doesn't answer.

## Authoritative sources

Full text bundled in this skill: `references/sources/eo-13556.md`, `references/sources/32-cfr-part-2002.md`, and (for CMMC's side of the picture) `references/sources/32-cfr-part-170.md`. Not bundled — fetch live: `esd.whs.mil` for DoDI 5200.48 and DoDI 5230.24; `archives.gov/cui` for the CUI Registry, Marking Handbook, and Executive Agent guidance (the Registry is a living database, not a fixed publication, so it was never a bundling candidate); the DoD CUI Registry for DoD-specific indexes; `acquisition.gov` for DFARS clause text; `federalregister.gov` for rulemaking status (e.g. the pending FAR CUI rule, FAR Case 2017-016). Trade press and law firm alerts are useful for noticing that something changed — confirm the substance in the primary source before it reaches a client.
