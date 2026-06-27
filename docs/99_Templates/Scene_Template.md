# Scene Template

> Usage: Copy this file for every new scene. Fill in all bracketed fields. Remove instructional comments (lines starting with >) before finalizing. Delete any optional sections that do not apply.

---

## Metadata

| Field | Value |
|---|---|
| Story Package | package_id |
| Chapter | chapter_XX |
| Scene ID | scene_XXX |
| Primary Purpose | Information \| Emotion \| Character \| Decision \| Discovery \| Conflict \| Consequence |
| Author | |
| Status | Draft \| In Review \| Approved \| Locked |

> Exactly one Primary Purpose per scene. Mandatory per Engine Core Specification §3. Must not be blank or combined with another purpose.

> Status definitions:
> - Draft — content in active authoring, not yet reviewed.
> - In Review — complete draft submitted for editorial/continuity review.
> - Approved — reviewed and accepted; safe to reference from other scenes.
> - Locked — finalized and shipped in a released package version. Locked scenes must not be edited in place; structural or narrative changes require a new package version and a full Continuity regression pass.

> Story Package must match a packageId declared in that package's manifest (Engine Core Specification §2.2). Chapter is a Story-Package-level organizational grouping for authoring and navigation only — the engine has no concept of "chapter"; it is not an engine data field and must never appear in a Condition or Consequence.

---

## Narrative Text

> Mandatory. This is the prose the player reads. A scene without narrative text is invalid.

[Write the scene's narrative text here.]

---

## Asset (Optional)

> Zero or one cinematic static image per scene. Delete this entire section if the scene has no asset.

| Field | Value |
|---|---|
| Asset ID | img_XXX |
| Type | image |
| URI | assets/images/scene_XXX.jpg |
| Alt Text | [Mandatory if asset is present — describe the image for accessibility] |

---

## Choices

> A scene must have either at least one Choice below, or exactly one Auto-Advance target — never both empty, never both filled.

### Choice: choice_XXX_a

| Field | Value |
|---|---|
| Label | [Player-facing choice text] |
| Visible If | [Optional condition — delete row if always visible] |
| Enabled If | [Optional condition — delete row if always enabled] |
| Next Scene | scene_XXX |

Consequences

> Every meaningful choice must define at least one consequence. Purely cosmetic choices (no state change) must be explicitly flagged as such in Writer Notes, not left silently empty.

| Variable ID | Operation | Value | Hidden? | Reveal Condition |
|---|---|---|---|---|
| var_example | set \| add \| subtract \| toggle \| append \| remove | [value] | yes \| no | [optional — only if Hidden: yes] |

> Variable category (Resource, Vitality, Knowledge, Progress, Social, Time, Inventory, Relationship, StateFlag) is declared once in variables.json and is not repeated here. Resolve category from Variable ID — do not duplicate it in this table.

> Operation must match the target variable's declared type (Engine Core Specification §5.2, §7.1) — e.g. toggle is only valid on boolean variables, append/remove only on Inventory/Relationship-style array variables.

> If any consequence is marked Hidden, it must still be fair in hindsight: the player must be able to reasonably infer that risk existed at the moment of choice, even without knowing the exact outcome. Document the fairness justification in Writer Notes.

> Premium-currency-related consequences may only alter method/odds-bearing variables (e.g. a Progress or probability-influencing Resource). They must never directly set a guaranteed-success StateFlag as a result of currency spend.

### Choice: choice_XXX_b

| Field | Value |
|---|---|
| Label | [Player-facing choice text] |
| Visible If | [Optional] |
| Enabled If | [Optional] |
| Next Scene | scene_XXX |

Consequences

| Variable ID | Operation | Value | Hidden? | Reveal Condition |
|---|---|---|---|---|
| | | | | |

> Duplicate the Choice block for additional choices.

---

## Auto-Advance (Use only if no Choices are defined)

| Field | Value |
|---|---|
| Next Scene | scene_XXX |

---

## Writer Notes

> Internal authoring reference only. Not read by the engine.

- Dramatic intent: [What this scene is meant to make the player feel or understand]
- Why this Primary Purpose fits: [Justification]
- Cosmetic choices (if any): [List any choice with no consequence and explain why it is intentionally cosmetic]
- Hidden consequence fairness justification (if applicable): [Explain the foreshadowing/signal that makes the hidden outcome fair]
- Historical accuracy notes (if applicable): [Cite the basis for any historical claim or setting detail]
- Supernatural ambiguity (if applicable): [Confirm narrative keeps any supernatural element unconfirmed/ambiguous — the engine and story must never confirm supernatural explanations]
- Consistency check: [Confirm alignment with existing variables, characters, prior scene history, and other Writer Notes above]

---

## Continuity

> Mandatory for all scenes at "In Review" status or beyond. Exists to keep large, long-running story packages internally consistent as scene count grows into the hundreds. This section verifies consistency — it does not repeat data already declared in Choices or Auto-Advance.

| Field | Value |
|---|---|
| Previous Scene | [scene_id of the scene(s) that can lead here — list all if multiple entry paths] |
| Outgoing Paths Verified | [Confirm every nextScene / autoAdvanceTo declared above has been checked to exist in this Story Package and resolves to a valid scene — yes/no, plus reviewer/date] |
| Required Flags | [StateFlag / variable conditions that must already be true for this scene to
