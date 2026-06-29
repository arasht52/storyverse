
- **Blueprint** — The Chapter Blueprint defines this scene's purpose, dramatic function, characters, expected variable movement, and dependencies before any prose is written.
- **Scene Draft** — The writer produces the scene using Scene_Template.md, fulfilling the blueprint's assignment.
- **Review** — Editorial and continuity review against this standard, the relevant Chapter Blueprint, World_Bible.md, and Character_Bible.md.
- **QA** — Structural and systemic validation against Story_State_Machine.md, Narrative_Event_Catalog.md, and variables.json.
- **Approved** — The scene is accepted as correct and internally consistent, and may be referenced by other scenes.
- **Locked** — The scene is finalized and shipped in a released package version. A Locked scene may not be edited in place; any change requires a new version and a full continuity regression pass, per Scene_Template.md.

---

## Mandatory Rules

- Every Scene has exactly **ONE** Primary Purpose, drawn from the engine's defined Scene Purposes (Information, Emotion, Character, Decision, Discovery, Conflict, Consequence).
- Every Scene answers exactly **ONE** dramatic question. If a scene seems to need two, it must be split into two scenes.
- Every Scene advances the game. A scene that leaves the story, the character, the mystery, and the real-world pressure exactly as they were before is invalid.
- Every Scene must either:
  - Trigger exactly one Narrative Event from Narrative_Event_Catalog.md, **OR**
  - Prepare one specific future Narrative Event by satisfying part of that event's Required Active States or Required Variables/Flags.
- Every Scene must explicitly reference:
  - The Chapter Blueprint beat it fulfills
  - The Narrative Event it triggers or prepares
  - The Story State(s) active during it, per Story_State_Machine.md
- Every Scene must change at least one of the following, recorded in its Consequences and Continuity sections:
  - Resource
  - Relationship
  - Knowledge
  - Time
  - Emotion
  - State
  - Variable
  - Player understanding

  If a complete draft changes none of these, the Scene must be removed, not patched with cosmetic dialogue.
- Every Scene ends with a reason to continue — an open question, a pending risk, or an unresolved tension that pulls the player into the next scene.
- Every Scene must preserve ambiguity wherever it touches the central mystery or any unconfirmed supernatural element; ambiguity is a structural requirement, not a tone choice.
- No Scene may confirm a supernatural explanation, under any framing, including through implication, music-style stage direction, or a character's certainty.
- One cinematic image maximum per scene, per Engine_Core_Specification §9.
- No filler dialogue. Every line must do narrative work.
- Dialogue must arise from conflict, objective, or tension — never from a need to "fill space" or restate known information.
- Exposition must emerge naturally, through character need or conflict, never through a character explaining something only the player needs to hear.
- Every choice must have purpose; a choice that exists only to look like a choice is invalid.
- Every meaningful choice must create a consequence, per Scene_Template.md; purely cosmetic choices must be explicitly justified in Writer Notes, not left as an unmarked exception.
- Scene pacing must match its Primary Purpose — a Decision scene moves differently than an Emotion scene; pacing choices must serve the assigned purpose, not the writer's general style.
- Scene length should be proportional to dramatic weight — a scene preparing a chapter's Irreversible Commitment earns more space than a scene delivering a single piece of routine information.

---

## Scene Quality Checklist

- [ ] The scene's Primary Purpose matches exactly what the Chapter Blueprint assigned to this beat.
- [ ] The scene's dramatic question is singular and answerable by the scene's end.
- [ ] The scene's narrative text alone (without choices) makes its Primary Purpose legible.
- [ ] The triggered or prepared Narrative Event is named explicitly in the scene's Continuity section.
- [ ] All Story States listed as active are consistent with Story_State_Machine.md's Allowed Previous States for this point in the chapter.
- [ ] At least one of Resource, Relationship, Knowledge, Time, Emotion, State, Variable, or Player Understanding visibly changes.
- [ ] Every character present behaves consistently with their Character_Bible.md role, motivation, and Moral Boundaries.
- [ ] All dialogue is traceable to a specific conflict, objective, or tension present in the scene.
- [ ] No line of dialogue or narrative text could be deleted without losing information or tension.
- [ ] All choices lead to genuinely different downstream consequences, not cosmetically different phrasing of the same outcome.
- [ ] Any hidden consequence has a prior, visible signal elsewhere in the scene or chapter, per Scene_Template.md fairness requirements.
- [ ] The scene ends on an open thread, risk, or question, not a settled, closed beat.
- [ ] Nothing in the scene confirms or forecloses the supernatural interpretation of any ambiguous event.
- [ ] At most one cinematic image is referenced, with mandatory alt text if present.
- [ ] Pacing (sentence rhythm, scene length, choice density) is appropriate to the assigned Primary Purpose.

---

## Common Mistakes

- **Multiple purposes** — a scene that tries to deliver Information and Decision and Emotion at once, diluting all three.
- **Repeated information** — restating something the player or Daniel already knows, without new framing or stakes.
- **No narrative movement** — a scene that reads well but leaves every variable, relationship, and piece of knowledge unchanged.
- **Empty dialogue** — exchanges that exist for atmosphere or characterization alone, with no conflict, objective, or tension driving them.
- **Forced exposition** — a character explaining backstory or rules a real person in their position would never volunteer aloud.
- **Artificial choices** — two options that lead to the same consequence, or a choice with no plausible reason for a real person to pick the "wrong" one.
- **State inconsistency** — a scene assuming a Story State is active before its Narrative Event has fired, or after it should have exited.
- **Variable inconsistency** — referencing a variable ID, category, or type that does not match variables.json.
- **Character inconsistency** — a character acting against their defined motivation, moral boundary, or established trust level without an authored reason.
- **Mystery inconsistency** — a scene that lets a detail slip which would only make sense under one interpretation of the central ambiguity.

---

## Scene Approval Checklist

Before a scene may move from QA to Approved, the following must each be independently verified:

- **Narrative** — The scene fulfills its assigned Chapter Blueprint beat and answers its single dramatic question.
- **Continuity** — Previous Scene, Outgoing Paths Verified, Required Flags, Continuity Risks, and Regression Check are all complete per Scene_Template.md.
- **Variables** — Every variable referenced exists in variables.json with matching category, type, and valid operation per Engine_Core_Specification §5–§7.
- **States** — Every Story State referenced is consistent with Story_State_Machine.md's Allowed Previous/Next States at this point in the chapter.
- **Events** — The triggered or prepared Narrative Event is correctly identified per Narrative_Event_Catalog.md, with all Required Active States and Required Variables/Flags genuinely satisfied.
- **Characters** — Every character's behavior, dialogue, and disclosed information is consistent with Character_Bible.md and any individual character file.
- **Historical accuracy** — Any historical or geographical claim is verifiable against the package's research documents.
- **Ambiguity** — No element of the scene tips the central mystery decisively toward either a supernatural or a purely psychological resolution.
- **Emotional progression** — The scene's emotional register is consistent with its chapter's defined Emotional Goal and represents real movement from the prior scene.
- **Player agency** — Choices are meaningful, distinguishable in consequence, and free of artificial constraint.
- **Production readiness** — The scene is free of placeholder text, unresolved bracketed fields, and unfinished Continuity or QA sections.

---

This standard applies to every Scene in every Story Package built on the StoryVerse engine and is binding regardless of genre, tone, or setting.
