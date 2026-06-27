# Character Template

> Usage: Copy this file for every new character. Fill in all bracketed fields. Remove instructional comments (lines starting with >) before finalizing. Delete any optional sections that do not apply.

---

## Metadata

| Field | Value |
|---|---|
| Character ID | character_XXX |
| Story Package | package_id |
| Role | Protagonist \| Antagonist \| Major \| Minor \| Recurring \| One-Off |
| Status | Draft \| In Review \| Approved \| Locked |
| Author | |

> Character ID must be unique within its Story Package and stable for the character's lifetime — do not reuse or recycle a retired Character ID.

> Status definitions follow Scene_Template.md conventions:
> - Draft — content in active authoring, not yet reviewed.
> - In Review — complete draft submitted for editorial/continuity review.
> - Approved — reviewed and accepted; safe to reference from scenes.
> - Locked — finalized and shipped in a released package version. Locked characters must not be edited in place; changes require a new package version and a full Continuity regression pass.

---

## Basic Information

| Field | Value |
|---|---|
| Display Name | [Name shown to the player] |
| Aliases | [Other names, titles, or nicknames used in-story, if any] |
| Age | [Age or age range at first appearance] |
| Gender | |
| Nationality | |
| Occupation | |

---

## Physical Description

- Appearance: [Build, face, hair, notable physical traits]
- Clothing: [Default/signature clothing; note if clothing varies by scene or status]
- Distinguishing Features: [Scars, marks, mannerisms, or anything that makes the character visually identifiable]

> If this character has an associated portrait or scene asset, reference the Asset ID per Engine_Core_Specification §9 in Gameplay Notes — do not embed image data in this file.

---

## Personality

- Traits: [Core personality traits — keep concise and specific]
- Strengths: [What this character is good at / relies on]
- Weaknesses: [Flaws that can be narratively exploited]
- Fears: [What this character avoids or dreads]
- Motivations: [What drives this character's choices]
- Internal Conflict: [The unresolved tension this character carries through the story]

---

## Narrative Role

- Function in Story: [Why this character exists structurally — e.g. mentor, obstacle, mirror, catalyst]
- Character Arc: [Where this character starts and where they are intended to end up, if applicable]
- Secrets: [Information this character is hiding from other characters]
- Public Knowledge: [What other characters and the player generally know about this character]
- Hidden Knowledge: [What only specific characters, or only the player via discovery, may know]

> Secrets and Hidden Knowledge must remain narratively ambiguous where they touch on any unconfirmed supernatural element — per Project_Brief, no supernatural explanation may ever be confirmed.

---

## Relationships

| Character | Relationship Type | Trust | Notes |
|---|---|---|---|
| character_XXX | [e.g. Ally, Rival, Family, Mentor, Romantic, Antagonist] | [Initial value or range — must correspond to a Relationship-category variable per Core_Abstraction_Model] | [Context, history, tension, or conditions that alter this relationship] |

> Trust values referenced here are narrative-design intent only. The authoritative value lives in the corresponding Relationship variable defined in variables.json — this table must stay consistent with that source, not duplicate it as a second source of truth.

---

## Dialogue Guide

- Speaking Style: [Formal/informal, blunt/evasive, rhythm, tone]
- Vocabulary: [Word choices, jargon, dialect, language quirks]
- Emotional Range: [How visibly this character expresses emotion, and under what conditions it shifts]
- Things Never Said: [Words, topics, or phrasing this character would never use — guardrails for consistency across writers]
- Recurring Expressions: [Catchphrases, verbal tics, or repeated phrasing, if any]

---

## Gameplay Notes

> Documentation only. Do not include engine logic or executable expressions in this section — reference variable/flag IDs as data points, not as code.

- Variables Affected: [List of variable IDs this character's scenes/choices typically modify, with category per Core_Abstraction_Model]
- Flags Related: [StateFlag IDs that track this character's status, e.g. has_met, is_alive, is_hostile]
- Inventory Interactions: [Items this character gives, takes, trades, or gatekeeps]
- Scene Appearances: [List of Scene IDs this character appears in — maintain as the character's roster grows]

---

## Continuity

> Mandatory for all characters at "In Review" status or beyond. Exists to keep large rosters of characters internally consistent as the cast grows into the hundreds. This section verifies consistency — it does not repeat data already declared in Gameplay Notes.

| Field | Value |
|---|---|
| First Appearance | [Scene ID] |
| Last Appearance | [Scene ID, or "Ongoing" if still active in unwritten scenes] |
| Required Story Conditions | [Variables/flags that must be true for this character to logically appear or behave as written] |
| Continuity Risks | [Anything about this character that could break if upstream scenes/variables change — e.g. assumes a specific Relationship value, assumes character is alive, assumes prior knowledge the player may not have] |
| Regression Check | [Date / author of last verification that this character remains consistent across all listed Scene Appearances; re-run whenever a referenced variable, scene, or Locked package version changes] |

---

## Writer Notes

> Internal authoring reference only. Not read by the engine.

- Historical accuracy notes: [Cite the basis for any historical claim, role, or setting detail tied to this character]
- Research references: [Sources consulted for realism/grounding]
- Continuity notes: [Any additional context future writers need before modifying this character]

---

## QA Checklist

> Complete before moving Status from Draft to In Review. Does not replace the Regression Check above.

- [ ] Character ID is unique and not reused from a retired character
- [ ] Display Name and Basic Information fully populated
- [ ] Physical Description is specific enough for consistent portrayal across scenes
- [ ] Motivations and Internal Conflict are defined and distinct from other characters
- [ ] Secrets, Public Knowledge, and Hidden Knowledge do not contradict each other
- [ ] No supernatural explanation is confirmed anywhere in this file
- [ ] Relationships table values match the corresponding Relationship variables in variables.json
- [ ] Dialogue Guide is specific enough to keep voice consistent across multiple writers
- [ ] All Variables Affected and Flags Related are declared in variables.json
- [ ] Scene Appearances list is current and matches actual scene references
- [ ] First Appearance / Last Appearance are accurate
- [ ] Continuity Risks reviewed against current upstream and downstream scenes

---

> Engine boundary reminder: This file is Story Package content only. Character traits, dialogue, relationships, and narrative meaning defined here are not known to the engine — the engine only reads structural references (variable IDs, flag IDs, scene IDs) per Engine_Core_Specification §12. Do not introduce engine logic, scripts, or executable expressions in this file.
