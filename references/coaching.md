# Coaching Non-Technical Stakeholders

The people who fund CMMC work are usually owners, CFOs, and operations leaders at companies of 20 to 500 people. They are not skeptical of security; they are skeptical of spending on something whose benefit they cannot see and whose requirement keeps moving. Explanations that work respect both of those things.

## Framings that hold up

**"CUI is the customer's information, not yours."** The single most useful reframe. The Government gave the client drawings and specs and attached conditions to holding them, the way any customer might. That makes the obligation contractual rather than regulatory in feel, which is both more accurate and easier to accept.

**"The score is a map, not a grade."** Executives hear 61 out of 110 and think 55%. Explain that the scale runs down to −203, that the number weights requirements by impact, and that what matters is which items are missing. Then show them the two or three 5-pointers.

**"Scope is the budget lever."** The 110 requirements are not negotiable; the number of systems they apply to is. This is the conversation that saves clients the most money and the one they arrive least prepared for.

**"Documented, implemented, demonstrable."** Three words that explain why the client's existing policy binder is not compliance and why their well-run network is not either. Assessors need all three.

## Requirements clients push back on, and what actually helps

**Multifactor authentication.** Rarely the technical objection it presents as — it's a change-management objection about the shop floor. Useful move: separate the users. Office and engineering staff can adopt it in a week; shared production terminals need a designed answer (badge readers, session-based access, or moving the terminal out of scope). Cost signal: low, if scoped thoughtfully.

**FIPS-validated encryption.** The requirement clients most often assume they meet and most often don't — "we use BitLocker" is not the same as "BitLocker in FIPS mode with a validated module." Worth catching early, because it is a 3-point item that can only be POA&M'd under the narrow SC.L2-3.13.11 exception, and only when encryption is already in place. Cost signal: low on modern endpoints, potentially high on legacy and embedded systems.

**Audit logging.** Clients hear "we need to buy a SIEM." Sometimes true, often not at the scale of a small enclave. The requirement is that specified events are captured, retained, protected, and *reviewed* — the review is the part that gets skipped and the part an assessor will ask to see evidence of. Cost signal: moderate; recurring effort more than capital.

**Email and file sharing.** Commercial M365 does not satisfy CUI handling. This is frequently the largest single line item for a small client and the one that most surprises them, so raise it early rather than late in a proposal. Cost signal: high, recurring, and it changes user workflow.

**Legacy manufacturing equipment.** The fear is "we'll have to replace the machines." Usually not — Specialized Assets are documented and isolated rather than assessed against the requirements. The isolation is real work, but it is a fraction of replacement. This is often the most reassuring thing you can tell a manufacturing client, and it is worth saying unprompted.

**Subcontractor flowdown.** Primes are frequently unaware they carry an obligation to flow requirements down, and that their exposure includes their suppliers' handling of CUI they passed along. Frame it as supply chain, not paperwork.

## Handling "is this even still required?"

Clients read trade press about pauses, suspensions, and reform and reasonably conclude they can wait. The honest answer has two parts:

1. The DFARS 252.204-7012 obligations — implement 800-171, report incidents within 72 hours, flow down to subcontractors — have been in force since 2017 and were untouched by both the CMMC suspension and the February 2026 clause reorganization. A client with no CMMC obligation today may still be non-compliant today. (Check `program-status.md` before citing clause numbers; several were renumbered or deleted in February 2026.)
2. The control baseline is stable even when the assessment mechanism is not. Work done against 800-171 keeps its value under any plausible restructuring. What is genuinely uncertain is *how* and *when* compliance gets verified, not *what* is required.

Do not oversell certainty in either direction. Clients who were told a hard deadline that then moved are the hardest to advise afterward, and that credibility is worth more than the urgency it buys.

## Tone

Direct, concrete, and non-condescending. These are people who run complex operations; they are new to this domain, not slow. Name real costs honestly — an advisor who tells a client that a hard thing is easy loses the relationship the moment the invoice arrives.
