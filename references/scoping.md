# Scoping

Source: CMMC Scoping Guide – Level 2, Version 2.13 (September 2024), implementing 32 CFR § 170.19. Cite by version; it is revised. Level 1 and Level 3 have separate scoping guides and different rules — do not apply this one across levels. Full text of both the guide and the rule are bundled at `references/sources/cmmc-scoping-guide-l2-v2.13.md` and `references/sources/32-cfr-part-170.md` — quote from them directly for exact wording rather than reconstructing it here.

Scoping is where CMMC engagements succeed or fail economically. The controls are fixed; the boundary is the variable, and it drives cost more than any other decision. Most of the value a good advisor adds is here.

## Before any of this: is it even a non-Federal system?

There is a prior question that precedes every asset category below. 32 CFR § 2002.14(h) splits information systems into **Federal** and **non-Federal**, and a system a contractor operates *on behalf of an agency* is a Federal information system — subject to FIPS 200 and SP 800-53, not SP 800-171. DFARS 252.204-7012(b)(1) mirrors the split, routing systems operated on behalf of the Government to requirements specified elsewhere in the contract and cloud services to DFARS 252.239-7010.

If a client is running a system on the government's behalf, the 110 requirements and the categories below are the wrong yardstick entirely. Resolve this first. See `cui-program.md` for the text and the "incidental receipt" carve-out that keeps most ordinary suppliers on the non-Federal side.

Note also that **classified assets are outside the CMMC Program's scope entirely**, even if they contain CUI.

## The five asset categories

Per 32 CFR § 170.19(c)(1) Table 3. Four are in scope, one is not.

**CUI Assets** — process, store, or transmit CUI. The guide defines each verb: *process* means CUI can be used by the asset (accessed, entered, edited, generated, manipulated, printed); *store* means CUI is inactive or at rest (electronic media, component memory, or physical paper); *transmit* means CUI is being transferred between assets, by physical or digital transport. **Assessed against all Level 2 requirements.**

**Security Protection Assets (SPAs)** — provide security functions or capabilities to the assessment scope. **Assessed against the Level 2 requirements relevant to the capabilities provided.** The guide's examples span three asset types, and the People and Facilities entries are the ones clients never anticipate:

- *People* — consultants providing cybersecurity services, managed service provider personnel who implement system maintenance, enterprise network administrators.
- *Technology* — cloud-based security solutions, hosted VPN services, SIEM solutions.
- *Facilities* — co-located data centers, Security Operations Centers, **OSA office buildings**.

**Security Protection Data (SPD)** is data stored or processed by SPAs that is used to protect the assessed environment — security-relevant information that could aid an attacker if disclosed. It includes configuration data required to operate an SPA, log files generated or ingested by an SPA, data on the configuration or vulnerability status of in-scope assets, and passwords granting access to the in-scope environment. SPD matters because it independently drags providers into scope: see the ESP rules below.

**Contractor Risk Managed Assets (CRMAs)** — can, but are not intended to, process/store/transmit CUI, because of security policy, procedures, and practices in place. **Not required to be physically or logically separated from CUI Assets.** The assessment treatment is conditional: the assessor reviews the SSP, and if sufficiently documented does not assess them against other requirements. But if documentation is insufficient, or if the risk-based policies or other findings raise questions, **the assessor may conduct a limited check to identify deficiencies**, assessed against CMMC requirements. The guide adds a constraint worth knowing: limited checks *shall not materially increase the assessment duration nor the assessment cost*. CRMA is therefore not a loophole — it is a documentation bet, and a thin SSP loses it.

**Specialized Assets** — can process, store, or transmit CUI but are unable to be fully secured. **Documented, reviewed via SSP, and not assessed against other CMMC requirements.** Five defined types:

- *Government Furnished Equipment (GFE)* — equipment owned or leased by the government, including OSA-acquired equipment built to government-required specifications or configurations. Excludes intellectual property and software (FAR 52.245-1).
- *IoT / IIoT* — interconnected devices with sensing/actuation capability and programmability, per NIST SP 800-172A. Includes smart electric grids, lighting, HVAC, fire and smoke detectors.
- *Operational Technology (OT)* — programmable systems or devices that interact with the physical environment, per NIST SP 800-160v2 Rev 1. Includes industrial control systems, building management systems, fire control systems, physical access control mechanisms, and explicitly SCADA.
- *Restricted Information Systems* — systems configured based on government security requirements to support a contract (fielded systems, obsolete systems, product deliverable replicas).
- *Test Equipment* — hardware and associated IT components used in testing products, system components, and contract deliverables (oscilloscopes, spectrum analyzers, power meters, special test equipment).

A Specialized Asset **may be eligible for an Enduring Exception** — and per the Assessment Guide, an enduring exception described with its mitigations in the SSP is assessed **MET**. That combination is the strongest reassurance available to a manufacturing client.

**Out-of-Scope Assets** — cannot process, store, or transmit CUI *and* do not provide security protections for CUI Assets, and are physically or logically separated. **No documentation requirements**, but the OSA must be **prepared to justify the asset's inability** to store, process, or transmit CUI. An asset that falls into any in-scope category cannot be reclassified as out of scope.

The guide gives one specific and extremely useful example: **an endpoint hosting a VDI client configured to allow no processing, storage, or transmission of CUI beyond keyboard/video/mouse is an Out-of-Scope Asset.** That single sentence is the architectural basis for the thin-client enclave pattern, and it is worth quoting to clients directly.

## Documentation obligations — the nuance consultants get wrong

For CUI Assets, SPAs, CRMAs, and Specialized Assets alike, the OSA must:

- document **each asset in an asset inventory** — and the guide says explicitly, for every category, that **there is no requirement to embed each asset in the SSP**;
- document the **treatment** of these assets in the SSP (for Specialized Assets, specifically showing they are managed under the OSA's risk-based policies, procedures, and practices);
- provide a **network diagram of the CMMC Assessment Scope** to facilitate scoping discussions during pre-assessment.

Clients frequently believe every asset must appear in the SSP and build an unmaintainable document. Inventory carries the assets; the SSP carries their treatment.

The assessor reviews the SSP to verify Specialized Assets are managed appropriately and accounted for in scope. **The assessor will not retain a copy of the SSP.**

## Separation

Separation is required **only for Out-of-Scope Assets**. By separating assets, the assessment scope shrinks — that is the entire economic lever.

- **Logical separation** — data transfer between physically connected assets is prevented by non-physical means: firewalls, routers, VPNs, VLANs.
- **Physical separation** — no connection at all, wired or wireless; data moves manually (e.g. USB drive).

The guide grounds this in SP 800-171 Rev 2's own language about isolating designated components into a separate CUI security domain, and notes the point of doing so is to provide adequate security for CUI *without* raising the whole organization's posture beyond what its missions require. That is the authoritative basis for recommending an enclave — it is NIST's own stated rationale, not a consultant's cost-saving improvisation.

## Enclaves and inheritance

Satisfying requirements through enterprise-wide people, processes, or technology does **not** automatically pull the whole enterprise into scope. The guide's worked example: a centralized IT group deploys a standard anti-malware tool; the tool, the people maintaining it, the deployment processes and policies, and supporting systems such as the management server could be in scope, while other enterprise functions and assets are not.

Within an enclave the OSA decides which requirements are implemented locally and which are inherited — **but all requirements must be MET**. If a process, policy, tool, or technology within the enclave would invalidate an enterprise-level implementation, that requirement cannot be inherited and must be met another way.

There is **no established metric for inherited implementations** from enterprise to enclave. The OSA determines the architecture that fits its business and complies. That absence of a bright line is worth flagging honestly rather than inventing a threshold.

## External Service Providers

An ESP is in the OSA's scope if it meets CUI Asset and/or Security Protection Asset criteria. Per 32 CFR § 170.19(c)(2), **to be considered an ESP, data — specifically CUI or Security Protection Data — must reside on the ESP's assets.** That SPD prong is what pulls in SIEM and log-management providers that never touch CUI.

The rule's own decision table — 32 CFR § 170.19(c)(2)(i), Table 4 — frames it by what the ESP touches, not just whether it's a CSP:

| When the ESP processes, stores, or transmits… | …and is a CSP | …and is NOT a CSP |
|---|---|---|
| **CUI** (with or without SPD) | The CSP shall meet the FedRAMP requirements in 48 CFR 252.204-7012 | The services provided are in the OSA's assessment scope and shall be assessed as part of the OSA's assessment |
| **SPD only** (no CUI) | The services provided are in the OSA's assessment scope and shall be assessed as Security Protection Assets | Same — assessed as Security Protection Assets |
| **Neither CUI nor SPD** | Does not meet the CMMC definition of an ESP | Does not meet the CMMC definition of an ESP |

The Scoping Guide's own narrative version of this (useful for explaining it to a client) collapses to the same outcomes:

| | Stores/processes/transmits CUI | Does NOT |
|---|---|---|
| **Is a CSP** | Must meet FedRAMP requirements in DFARS 252.204-7012 | Not required to meet those FedRAMP requirements; services still in the OSA's assessment scope |
| **Not a CSP** | Requires assessment; the ESP services used to meet OSA requirements are in the OSA's scope | No separate CMMC assessment; services still in the OSA's assessment scope |

The rule text adds one detail the guide's prose doesn't spell out as crisply: **an ESP may voluntarily undergo a CMMC certification assessment to reduce the OSA's assessment effort**, and the *minimum* assessment type required of the ESP is dictated by the OSA's DoD contract requirement — so an ESP can always choose to go further than the floor.

Additional rules from the guide:

- An ESP may **voluntarily request a C3PAO assessment** as a business decision.
- **Staff augmentation where the OSA provides all processes, technology, and facilities does not need a CMMC assessment.**
- ESPs can sit inside the same corporate structure yet still be external to the OSA — a centralized SOC or NOC serving multiple business units. Same rules apply.
- **Not every service provider is an ESP.** HR and accounting SaaS typically neither contribute to the security of the environment, nor process or store SPD, nor touch CUI. The OSA determines ESP status from the services provided and the data involved.
- The OSA is assessed against its **on-premises infrastructure connecting to the CSP**, and the CRM's security requirements must be documented or referenced in the SSP, which is also assessed.
- When ESPs are assessed as part of the OSA's assessment, the assessment type is dictated by the OSA's solicitation and contract requirement.

Definitions the guide draws carefully: a **CSP** provides its own cloud services (on-demand access to a shared pool of configurable computing resources). An ESP that is not a CSP and provides technical support is a **Managed Service Provider** — it does not host its own cloud platform, and an ESP may use cloud offerings to deliver services without being a CSP. **An ESP that manages a third-party cloud on behalf of an OSA is not a CSP.**

Required documentation for ESP relationships: the use of the ESP, its relationship to the OSA, and the services provided must be in the OSA's SSP and described in the ESP's **service description and customer responsibility matrix (CRM)**. Evaluate the CRM to see which objectives the provider owns and which the OSA owns, and consider the SLAs, MOUs, and contracts supporting the OSA's security objectives.

Separately from CMMC scoping, DFARS 252.204-7012(b)(2)(ii)(D) requires a contractor using an external CSP for covered defense information to ensure the provider meets **FedRAMP Moderate baseline equivalency** and complies with the clause's incident reporting, media preservation, forensic access, and damage assessment paragraphs. Equivalency is a demanding bar and vendor claims of "FedRAMP equivalent" should be treated as unverified until an evidence package exists. Verify DoD's current position before advising — this guidance has been contested and revised.

## SIEM and log storage — a worked case from the guide

Aggregated logs in a SIEM are SPD; the SIEM is the SPA, and it is in the assessment scope. Because SIEMs vary (on-premises appliance, virtual appliance, cloud), assessment methods vary. If the SIEM or its log data is hosted or maintained by an ESP, **the portion of the ESP providing the SIEM service or log storage is in the OSA's assessment scope**. Hot storage is typically collocated with the SPA; cold storage is typically offline or in cloud storage — and **the method and location of cold storage are also in scope**. Clients routinely forget the archive.

## Level relationships and use cases

- **A Level 2 assessment satisfies Level 1 for the same scope.** If FCI and CUI share the Level 2 scope, the Level 2 implementations count toward the Level 1 objectives. If FCI and CUI are in different environments, the two assessments are conducted independently and implementations do not carry across.
- **CRMAs in a Level 2 scope are treated as CUI Assets if they fall within a Level 3 scope.** An OSC may choose to designate them as CUI Assets for the Level 2 certification assessment and have a C3PAO assess them.
- Specialized Asset requirements **differ between Level 2 and Level 3**; an OSC may have them assessed by a C3PAO during the Level 2 assessment. CRMAs and Specialized Assets not assessed to Level 3 scoping requirements during the Level 2 assessment undergo **limited checks** during the DIBCAC Level 3 assessment, where DIBCAC may check any Level 2 requirement of any in-scope asset.
- A Level 2 POA&M must be closed out and **Final Level 2 (C3PAO)** achieved before initiating a Level 3 certification assessment. If Level 3 is the eventual goal, consult the Level 3 Scoping Guide *before* setting the Level 2 boundary.

## Reassessment triggers

A new assessment is required for significant architectural or boundary changes — network expansions, mergers and acquisitions. Operational changes within the scope that follow the existing SSP do not trigger reassessment and are covered by annual affirmations of continuing compliance.

## Questions that change the answer

When scoping advice is requested, these are usually the facts you need first:

- What CUI does the client actually receive, in what form, and from whom?
- Where does it land first — email, a portal, physical media?
- Which business processes touch it, and which systems support those processes?
- Who administers the environment, and is any of it outsourced? Does any provider hold CUI *or SPD*?
- What is on the shop floor, and does it fall within a Specialized Asset definition?
- Is there existing separation the client already trusts, or would the enclave be new?
- Is Level 3 a realistic future requirement for this client?
