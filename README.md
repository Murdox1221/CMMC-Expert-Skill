# CMMC-Expert

A Claude Skill providing authoritative, citation-grounded expertise on **CMMC**, **NIST SP 800-171 / 800-172**, and the **CUI Program** for the U.S. defense industrial base.

The skill has two jobs: answer authoritatively from U.S. Government primary sources, and coach non-technical stakeholders. It **never renders a MET / NOT MET or compliance determination** on a user's specific facts — that boundary is enforced by a hard rule in `SKILL.md`.

## Layout

```
SKILL.md                          Entry point: instructions + frontmatter
references/
  levels-and-controls.md          Levels, families, assessment objectives, Rev 2 vs Rev 3
  scoring-and-poams.md            SPRS scoring, point values, POA&M eligibility, affirmations
  scoping.md                      Asset categories, enclaves, ESPs/CSPs, FedRAMP equivalency
  assessment-methodology.md       Examine/interview/test, evidence rules, finding categories
  control-lineage.md              SP 800-53 -> SP 800-171 derivation, tailoring, ODPs
  cui-program.md                  32 CFR Part 2002, CUI Registry, Basic vs Specified, marking
  program-status.md               Phase-in, clause numbering, rulemaking (volatile - always web-check)
  coaching.md                     Framings for non-technical client stakeholders
  sources/                        Full text of the government primary sources
    32-cfr-part-170.md            CMMC Program rule
    32-cfr-part-2002.md           CUI Program rule
    cmmc-assessment-guide-l2-v2.13.md
    cmmc-scoping-guide-l2-v2.13.md
    eo-13556.md                   Executive Order 13556
    sp-800-171r2-to-800-53r4-mapping.md  DEFAULT: Rev 2 Appendix D -> parent 800-53 Rev 4 control(s)
    sp-800-53-rev4-cui-parents.md        DEFAULT: Control text + Supplemental Guidance, 800-53 Rev 4 parents
    sp-800-171r3-to-800-53r5-mapping.md  SECONDARY LENS: 800-171 Rev 3 -> 800-53 Rev 5 mapping
    sp-800-53-rev5-cui-parents.md        SECONDARY LENS: Control text + Discussion, 800-53 Rev 5 parents
```

## Using the skill

Copy or symlink this directory into a Claude skills location (e.g. `~/.claude/skills/cmmc-expert/`), or install it wherever your Claude client loads skills from. `SKILL.md` must sit at the skill root with `references/` beside it.

## Maintenance notes

- **Stable vs volatile.** Control text, objectives, and scoring arithmetic change only through formal rulemaking — answer from the reference files. Program phase, clause numbers, and SPRS mechanics move often — `references/program-status.md` must be paired with a web search every time.
- **Interpretation is two-track.** When explaining what a control *means*, the skill must cite the parent SP 800-53 control. **Default:** SP 800-171 Rev 2 → SP 800-53 Rev 4 (`sp-800-171r2-to-800-53r4-mapping.md` from Appendix D, `sp-800-53-rev4-cui-parents.md` from NIST's Rev 4 OSCAL catalog) — this is the CMMC Level 2 basis. **Secondary lens:** SP 800-171 Rev 3 → SP 800-53 Rev 5 (`sp-800-171r3-to-800-53r5-mapping.md`, `sp-800-53-rev5-cui-parents.md`) — Rev 3 restated the same requirements against the current catalog and Rev 5's Discussion is often fuller. The skill leads with Rev 4 and names the revision on every quote. Seven Rev 2-cited enhancements are withdrawn in Rev 5 and flagged with their successor.
- **Not bundled:** DoDI 5200.48 and DoDI 5230.24 (source site blocks automated fetch); the full SP 800-53 catalog beyond the CUI parents; SP 800-171A; SP 800-172/172A. Add to `references/sources/` if needed.
- The `description` field in `SKILL.md` frontmatter must stay at or under 1024 characters or the skill fails to load.
