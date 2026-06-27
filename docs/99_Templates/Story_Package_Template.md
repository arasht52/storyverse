# Story Package Template

> Usage: Copy this file once per new Story Package and rename it to match the package (e.g. Story_Package_PersianTreasure.md). Fill in all bracketed fields. Remove instructional comments (lines starting with >) before finalizing. This document describes exactly one Story Package — a complete, independent playable game loaded by the engine. The engine itself never changes; only Story Packages change.

---

## Metadata

| Field | Value |
|---|---|
| Story Package ID | package_id |
| Display Name | [Player-facing title, e.g. "Persian Treasure"] |
| Version | 1.0.0 |
| Status | Draft \| In Review \| Approved \| Locked |
| Author | |

> Story Package ID must match the packageId declared in the package's manifest (Engine_Core_Specification §2.2) and remain stable across versions.

> Status definitions follow Scene_Template.md conventions:
> - Draft — actively in design, structure may still change.
> - In Review — complete draft submitted for editorial/continuity/QA review.
> - Approved — reviewed and accepted; safe to begin production at scale.
> - Locked — finalized and shipped in a released version. Structural changes require a new Version and a full regression pass across Scenes, Characters, and Variables.

---

## Story Summary

> A concise, spoiler-aware overview of the premise, setting, and central conflict. This is a production reference, not marketing copy.

[2–5 paragraphs describing the premise, setting, central conflict, and player's role.]

---

## Genre

[e.g. Historical Adventure, Mystery, Survival, Political Thriller]

---

## Themes

> Core ideas the package explores. Used to keep scene and character writing thematically consistent across a large team.

- [Theme 1]
- [Theme 2]
- [Theme 3]

---

## Tone

[e.g. Grounded, tense, melancholic, hopeful — describe the emotional register the package should consistently maintain.]

---

## Target Experience

> What the player should feel and understand by the end of a playthrough. Used as a north star for Scene purpose selection and ending design.

[Describe the intended emotional and narrative payoff.]

---

## Story Rules

> Setting-specific constraints that all writers on this package must follow. These are narrative rules, not engine rules.

- Historical accuracy requirements specific to this setting: [e.g. time period, real-world events referenced, what must remain historically grounded per Project_Brief]
- Realism boundaries: [What this package will and will not depict]
- Supernatural policy: [Must restate and comply with Project_Brief — no supernatural explanation may ever be confirmed within this package]
- Other package-specific narrative constraints: [e.g. tone restrictions, content the package avoids]

---

## Variable Mapping

> Maps the engine's abstract Variable Categories (Core_Abstraction_Model, Engine_Core_Specification §5) to this package's story-specific meaning. The engine only ever reads the abstract category and variable id/type — this table exists purely for writer and designer reference within this package.

| Engine Category | Story Meaning (this package) | Example Variable ID |
|---|---|---|
| Resource | [e.g. Money] | var_money |
| Vitality | [e.g. Health] | var_health |
| Knowledge | [e.g. Clues Discovered] | var_clues |
| Progress | [e.g. Mission Progress] | var_mission_progress |
| Social | [e.g. Reputation] | var_reputation |
| Time | [e.g. Days Remaining] | var_days_remaining |
| Inventory | [e.g. Carried Items] | var_inventory |
| Relationship | [e.g. Trust with [Character]] | var_trust_character_x |
| StateFlag | [e.g. Has Met Informant] | flag_met_informant |

> This table is documentation only. The authoritative definitions live in this package's variables.json per Engine_Core_Specification §5.2 — do not let this table drift out of sync; treat variables.json as the source of truth.

---

## Package Structure

> File/folder inventory for this package, following the structure defined in Engine_Core_Specification §2.1.

| Component | Location | Notes |
|---|---|---|
| Scenes | /scenes | One file per scene, per Scene_Template.md |
| Characters | /characters | One file per character, per Character_Template.md (production documentation; not engine-loaded directly) |
| Variables | /variables/variables.json | Per Variable_Template.md and Engine_Core_Specification §5.2 |
| Assets | /assets/images | One cinematic static image per scene maximum |
| Localization | /localization | Per-locale string tables, see Localization Notes below |
| Research | /research | Historical/setting reference material backing Story Rules |
| Endings | /endings | One entry per ending, see Ending List below |
| Achievements | /achievements | Achievement definitions tied to StateFlags/Progress variables |

---

## Chapters

> Organizational grouping for authoring and navigation only — "Chapter" has no engine meaning (Scene_Template.md, Metadata notes) and is not referenced in Conditions or Consequences.

| Chapter | Title | Summary | Scene Range | Status |
|---|---|---|---|---|
| chapter_01 | [Title] | [One-line summary] | scene_001–scene_0XX | Draft \| In Review \| Approved \| Locked |

---

## Ending List

> Every distinct ending state this package can produce. Each ending must be reachable through a documented combination of variables/flags.

| Ending ID | Name | Trigger Conditions | Tone | Notes |
|---|---|---|---|---|
| ending_001 | [Name] | [Variable/flag conditions required] | [e.g. Triumphant, Bittersweet, Tragic] | [Any additional context] |

---

## Asset Requirements

> Production tracking for the one-cinematic-image-per-scene rule (Engine_Core_Specification §9).

| Asset ID | Linked Scene | Description | Status | Notes |
|---|---|---|---|---|
| img_XXX | scene_XXX | [Brief visual description] | Not Started \| In Progress \| Final | [Alt text requirement, style reference, etc.] |

---

## Localization Notes

- Supported Locales: [List, e.g. en-US, fa-IR]
- Source Locale: [The locale all narrative text is authored in first]
- Strings Requiring Cultural Adaptation: [Idioms, historical references, or jokes that may not translate directly]
- Localization Status Tracking: [Reference to /localization status files or a tracking sheet]

---

## Accessibility Notes

- Alt Text Compliance: [Confirm all Asset Refs across this package have mandatory Alt Text per Engine_Core_Specification §9]
- Reading Level / Clarity: [Any package-specific guidance on sentence complexity, jargon]
- Color/Contrast Considerations: [If relevant to provided art direction]
- Other Accessibility Commitments: [Any package-specific accommodations]

---

## Production Checklist

> Tracks overall package completeness. Complements, not replaces, the per-file QA Checklists in Scene_Template.md and Character_Template.md.

- [ ] All Chapters defined with accurate Scene Ranges
- [ ] All Scenes authored to at least Draft status
- [ ] All Characters authored to at least Draft status
- [ ] variables.json complete and matches Variable Mapping table
- [ ] All Endings reachable and documented in Ending List
- [ ] Asset Requirements tracked for every scene with an asset
- [ ] Achievements defined and linked to valid variables/flags
- [ ] Research folder populated to support all Story Rules claims

---

## QA Checklist

- [ ] Every Scene passes its own Pre-Submission Checklist (Scene_Template.md)
- [ ] Every Character passes its own QA Checklist (Character_Template.md)
- [ ] No variable referenced anywhere in this package is undeclared in variables.json
- [ ] No scene reference (nextScene, autoAdvanceTo, Previous Scene) points to a nonexistent Scene ID
- [ ] No supernatural explanation is confirmed anywhere in this package
- [ ] No premium-currency consequence sets a guaranteed-success StateFlag directly (Engine_Core_Specification §7.1)
- [ ] Hidden consequences across the package are fair in hindsight (spot-checked across Chapters)
- [ ] Relationship table values in Character files match variables.json
- [ ] Historical accuracy claims in Story Rules and Writer Notes are sourced in /research

---

## Release Checklist

- [ ] Version number incremented per semver and matches manifest engineVersionRequired compatibility (Engine_Core_Specification §2.3, §11.9)
- [ ] All package contents pass QA Checklist above
- [ ] All Locales in Localization Notes are complete or explicitly marked partial
- [ ] Accessibility Notes commitments verified against actual asset/text content
- [ ] Final regression pass completed across all Scenes and Characters at Locked status
- [ ] Status updated to Locked only after all above items are confirmed
- [ ] Release notes/changelog entry recorded for this Version

---

> Engine boundary reminder: This file is Story Package content only. Genre, themes, variable meanings, chapters, and endings defined here are not known to the engine — the engine only reads structural data (scenes, choices, variables, conditions, consequences) per Engine_Core_Specification §12. Do not introduce engine logic, scripts, or executable expressions in this file.
