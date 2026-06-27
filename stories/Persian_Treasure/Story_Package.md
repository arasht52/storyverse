# Story Package: Persian Treasure

---

## Metadata

| Field | Value |
|---|---|
| Story Package ID | persian_treasure |
| Display Name | Persian Treasure |
| Version | 0.1.0 |
| Status | Draft |
| Author | StoryVerse Narrative Design Team |

---

## High Concept

A debt-burdened civil engineer travels to Iran's Khuzestan province to investigate a collapsing irrigation excavation and finds himself drawn into the buried route of an Achaemenid caravan lost in 474 BCE — forced to decide, scene by scene, whether the visions guiding him are inherited memory, psychological strain, or something he will never be able to prove either way.

---

## Game Vision

Persian Treasure is StoryVerse's flagship title: a grounded, historically researched narrative built entirely on consequence rather than spectacle. There are no combat systems, no supernatural confirmations, and no safety net. Every choice the player makes — financial, relational, professional — closes some doors permanently and opens others. The game's ambition is to prove that a branching narrative can deliver the tension of a thriller and the integrity of historical fiction without ever resorting to magic, fantasy resolution, or narrative cheats.

The player should finish the game uncertain whether the protagonist uncovered an ancient mystery or simply projected meaning onto financial desperation and physical exhaustion — and should feel that uncertainty was earned, not withheld.

---

## Core Pillars

- Story first. Every system exists to serve the narrative, never the reverse.
- Choices matter. No choice is reversible by design; consequences compound.
- Grounded realism. No abilities, no shortcuts, no narrative convenience.
- Historical accuracy whenever possible, particularly regarding Achaemenid Persia and Khuzestan.
- No confirmed supernatural events, ever, under any ending.
- Player immersion outweighs visual fidelity — one still image per scene, never more.
- Premium currency changes methods, never guarantees success.

---

## Narrative Premise

Daniel Farrokhi, a structural engineer with a collapsing personal finances and a stalled career, accepts a high-paying but ethically grey consulting contract: stabilize an unauthorized excavation near an irrigation project in Khuzestan before regulators or financiers discover the dig was never permitted. The excavation has exposed what appears to be a buried caravan route — and Daniel begins experiencing vivid, specific, historically accurate impressions of a 474 BCE Achaemenid caravan that should be impossible for him to know about.

As the excavation deepens, Daniel must manage three converging pressures simultaneously: the financial backers who want results regardless of risk, the historical truth of what actually happened to the caravan, and his own uncertainty about whether his "visions" are genuine inherited memory, a psychological response to stress and fatigue, or fabrication driven by financial desperation. The game never resolves which of these is true. It only resolves what Daniel did about it.

---

## Story Philosophy

Persian Treasure treats ambiguity as a design commitment, not a narrative cop-out. The inherited-memory thread is written so that every "supernatural-seeming" beat has at least one fully sufficient mundane explanation available to the player at the time it occurs — financial stress, sleep deprivation, prior research Daniel could plausibly have absorbed, family history he was never told directly. The engine and narrative never confirm which explanation is correct, in any ending, including the most "fantastical"-feeling one. The story's emotional payoff comes from how Daniel acts under uncertainty, not from resolving the uncertainty itself.

Consequences are never narrated as fair only in retrospect for spectacle — every hidden consequence is seeded with a prior, visible signal the attentive player could have caught, in compliance with the project's fairness-in-hindsight requirement.

---

## Setting

The excavation site sits in rural Khuzestan province, southwestern Iran, near the historical trade corridors linking the Persian Gulf to the Achaemenid heartland. The contemporary scenes are set in and around a modest provincial town: rented rooms, a half-funded engineering office, irrigation canals, and the excavation site itself. The ancient-caravan impressions are set along the same physical geography roughly 2,500 years earlier — arid plains, seasonal rivers, and a caravan route plausibly used for trade between Susa and the Persian Gulf during the reign of Artaxerxes I.

All historical and geographical claims about Khuzestan, Achaemenid trade routes, caravan composition, and the year 474 BCE are sourced from the Khuzestan historical and geographical research compiled for this package and are subject to the Story Rules governing historical authenticity.

---

## Time Period

Two interleaved timelines:
- **Contemporary** — present day, framing the entire playthrough.
- **474 BCE** — the Achaemenid caravan timeline, experienced only through Daniel's impressions, never as an independently playable "flashback" the engine treats as confirmed historical fact.

---

## Main Character

**Daniel Farrokhi** — a structural/civil engineer in his late thirties, second-generation Iranian-American, fluent in Persian but raised primarily in the diaspora. Financially overextended after a failed independent engineering venture, Daniel takes the Khuzestan contract primarily to resolve mounting personal debt, not out of any initial interest in history or heritage. His arc is defined by the tension between what he needs (money, professional rehabilitation) and what the excavation increasingly demands of him (honesty, risk, and confrontation with a family history he was never told).

Daniel is the engine's sole player-controlled character; all Relationship, Knowledge, and Resource variables in this package are tracked relative to him.

---

## Central Mystery

What happened to the Achaemenid caravan that vanished along this route in 474 BCE, and why does Daniel — a man with no formal historical training and no prior connection to this specific region that he is aware of — appear to know details about it that match the excavation findings before they are uncovered. The mystery is dual-layered: the historical fate of the caravan (which the game resolves with reasonable historical specificity), and the source of Daniel's knowledge (which the game deliberately never resolves).

---

## Core Gameplay Loop

1. **Information** scenes establish site findings, financial pressure, or historical context.
2. **Decision** scenes require Daniel to choose how to respond — professionally, financially, or personally.
3. Choices apply **Consequences** to Resource, Vitality, Knowledge, Progress, Social, Time, Inventory, Relationship, and StateFlag variables.
4. Accumulated state gates which **Discovery**, **Conflict**, **Character**, and **Consequence** scenes become reachable.
5. Premium currency may be spent to change the *method* available in a Decision scene (e.g., unlocking a riskier-but-faster excavation approach, or a costlier-but-safer one) — it never guarantees the outcome of that method succeeding.
6. Chapters conclude on irreversible state commitments that lock off alternative paths for the remainder of the playthrough.

---

## Story Structure

Four main chapters, each ending on an irreversible commitment that meaningfully narrows the remaining path space.

| Chapter | Title | Summary |
|---|---|---|
| chapter_01 | The Contract | Daniel arrives in Khuzestan, assesses the unauthorized excavation, and commits to the terms of his involvement — establishing his financial desperation and first unexplained impression. |
| chapter_02 | The Route | The excavation reveals physical evidence of the caravan route. Daniel's impressions grow more specific and historically precise, while financial backers escalate pressure to move faster than safety allows. |
| chapter_03 | The Ledger | Daniel uncovers a connection between his own family history and the region, forcing a reckoning between personal truth, financial survival, and the integrity of the excavation itself. |
| chapter_04 | What Was Carried | The excavation and the caravan's fate converge. Daniel makes his final, irreversible decision about what to disclose, to whom, and at what personal cost — determining which ending the player reaches. |

---

## Variable Mapping

| Engine Category | Story Meaning (Persian Treasure) | Example Variable ID |
|---|---|---|
| Resource | Money | var_money |
| Vitality | Physical and Mental Strain | var_strain |
| Knowledge | Historical/Site Understanding | var_site_knowledge |
| Progress | Excavation Progress | var_excavation_progress |
| Social | Professional Reputation | var_reputation |
| Time | Days Until Funding Deadline | var_days_remaining |
| Inventory | Carried Tools, Documents, and Artifacts | var_inventory |
| Relationship | Trust with Financiers, Crew, and Family | var_trust_[character] |
| StateFlag | Discrete Story States (e.g. flag_family_history_revealed, flag_excavation_reported) | flag_[event] |

This table is documentation only. The authoritative definitions for this package live in `stories/Persian_Treasure/variables/variables.json` per Engine_Core_Specification §5.2.

---

## Economy Philosophy

Money (Resource) is the primary real-world pressure driving Daniel's decisions throughout all four chapters — not a side mechanic. Nearly every Decision scene has some financial dimension, whether direct (accepting payment, paying crew, bribing officials) or indirect (time spent on the excavation is time not spent earning elsewhere). Premium currency in this package represents access to better *methods* — better equipment, more experienced local contacts, faster lab analysis — and is implemented exclusively through Consequences that modify Progress or probability-influencing Resource variables. No premium-currency consequence in this package ever directly sets a guaranteed-success StateFlag, consistent with Engine_Core_Specification §7.1.

---

## Failure Philosophy

There are no fail states that end the game prematurely. Failure in Persian Treasure means a worse but still playable continuation: a damaged relationship, a discredited reputation, a financial hole that narrows future choices, or a piece of historical truth permanently lost to a collapsed excavation. Every failure is narratively legible in hindsight — telegraphed by an earlier visible risk signal — even when its precise consequence was hidden at the time of choice.

---

## Ending Philosophy

Persian Treasure has multiple endings determined by the combination of Daniel's financial state, his relationships, how much of the historical truth was preserved versus destroyed, and what he ultimately discloses about his impressions. No ending confirms or denies the supernatural explanation for Daniel's knowledge of the caravan — every ending is written to be fully coherent under either the inherited-memory interpretation or the psychological-strain interpretation. Endings differ in emotional tone (e.g., professionally redeemed but personally isolated, financially ruined but historically vindicated, quietly reconciled with family at the cost of the excavation's credibility) rather than in providing a definitive metaphysical answer.

---

## Art Direction

One cinematic static image per scene, rendered in a muted, realistic palette that reflects Khuzestan's arid contemporary landscape and the visual texture of excavation sites — dust, exposed earth, harsh daylight, utilitarian equipment. The 474 BCE impression scenes share the same realistic rendering approach as the contemporary scenes rather than a stylized "dream" filter, reinforcing that the player should never receive a visual cue confirming which interpretation of Daniel's impressions is correct.

---

## Audio Direction

Minimal, diegetic-first sound design: wind, tools, distant machinery, and ambient site noise dominate over score. Music is used sparingly, primarily in Emotion and Consequence scenes, and never swells in a way that editorializes the supernatural-versus-psychological ambiguity — the score supports Daniel's emotional state, not a metaphysical verdict.

---

## Accessibility

All scene assets in this package require mandatory alt text per Engine_Core_Specification §9, with particular care taken to describe excavation and caravan imagery accurately without importing interpretive bias (alt text describes what is visually present, not whether it is "real"). Narrative text avoids unnecessarily dense academic phrasing despite the historical subject matter, keeping comprehension accessible without sacrificing accuracy.

---

## Localization

Source locale is en-US, with Persian (fa-IR) as a priority target locale given the setting and protagonist's background. Persian-language terms, place names, and historical titles used in dialogue are tracked for transliteration consistency across both locales. Cultural and historical references specific to Khuzestan are flagged for review by a culturally and historically informed localizer rather than direct machine translation.

---

## Production Status

Chapter 1 (The Contract) is in active scene authoring. Chapters 2–4 are structurally outlined at the chapter-summary level above and pending detailed scene breakdown. Variable definitions for core Resource, Vitality, Time, and StateFlag tracking are drafted; Relationship and Inventory variables tied to secondary characters are pending as those characters are authored. No scenes have yet reached Locked status.

---

## Future Expansion Notes

The Khuzestan historical research compiled for this package supports additional caravan-route content beyond the four main chapters, including possible epilogue content set further along the historical trade route or additional contemporary-timeline content following Daniel after the main story's conclusion. Any such expansion must preserve the established ambiguity policy and must not retroactively confirm or deny the supernatural interpretation established across the four main chapters.
