# Game Design Document: Persian Treasure

---

## High Concept

A grounded, choice-driven narrative game in which a financially desperate engineer's investigation of an illegal excavation forces the player to manage real-world consequence — money, trust, legal exposure, physical risk — while never being told whether the protagonist's growing connection to an ancient mystery is real or imagined.

---

## Design Vision

Persian Treasure is designed as a premium narrative experience that earns its tension entirely from consequence management, not from spectacle, combat, or puzzle mechanics. The design goal is a game where the player feels the same pressure Daniel feels: never enough money, never enough certainty, never a clean choice. Every system in this document exists to produce that feeling repeatedly, scene after scene, without ever resolving the central ambiguity that gives the game its identity.

---

## Target Player Experience

The player should feel like a person managing an unraveling situation under real constraints, not a hero solving a mystery with growing power. By the end of the game, the player should be able to articulate what Daniel did and why — and should not be able to say with confidence whether he was right to trust his impressions. The target experience is tension through scarcity and ambiguity, not tension through danger-of-death or twitch mechanics.

---

## Core Gameplay Loop

1. Player receives new information or pressure (financial, legal, relational, or historical).
2. Player makes a Decision-purpose choice that trades resources against risk.
3. Consequences shift the player's standing across Resource, Vitality, Knowledge, Social, Time, Inventory, Relationship, and StateFlag variables.
4. Shifted standing changes which paths, characters, and discoveries are accessible going forward.
5. Periodically, accumulated stress/fatigue and discovery converge into an ambiguous vision beat that deepens the mystery without resolving it.

This loop repeats at the scene level throughout all four chapters, escalating in stakes each chapter rather than changing in kind.

---

## Design Pillars

- **Scarcity over power.** The player never accumulates enough resources to feel safe; every gain is offset by a new pressure.
- **Consequence over choice volume.** Fewer, heavier decisions are preferred over many trivial ones.
- **Ambiguity as a designed system, not a narrative gap.** Every system touching the vision thread is built to support two equally valid readings at all times.
- **Realism as a constraint, not flavor.** No mechanic may exceed what a real, underfunded, unauthorized excavation could plausibly involve.
- **Method, not guarantee.** Any premium-currency interaction changes approach or odds, never outcome certainty.

---

## Player Motivation

The player is motivated by the same dual pull Daniel experiences: the practical need to resolve financial pressure, and the harder-to-name pull of wanting to know what is really happening with the visions. The game is designed so these two motivations are never fully alignable — solving one often costs ground on the other — so the player is always making a real tradeoff, not optimizing a single axis.

---

## Story Structure

Four chapters, each ending on an irreversible commitment. Structurally, each chapter is internally near-linear in scene sequence but variable-state-divergent, meaning the order of major beats is consistent across playthroughs while the player's standing entering each beat differs significantly. This keeps production scope controlled while preserving the feeling of consequence-driven divergence.

---

## Investigation Structure

Investigation is modeled as accumulation across three parallel Knowledge-category tracks: historical understanding, physical/engineering evidence, and personal/family knowledge. No single track unlocks the ending alone; the four endings are reached through different combinations of standing across all three, combined with Relationship and StateFlag outcomes. Investigation never resolves into a single "solved" state — it resolves into a final interpretive position the player has earned through accumulated choices.

---

## Progression Structure

Progression is chapter-gated, not level-gated. A chapter ends only when its Chapter Completion Conditions (defined per chapter) are met, regardless of how many scenes a given playthrough visited along variable-divergent paths. Progression is measured in variable standing carried forward, not in points, levels, or unlockable abilities — Daniel does not get mechanically stronger, only better or worse positioned.

---

## Choice Philosophy

Every Decision-purpose scene must present options that are each individually reasonable from some perspective — financial, ethical, relational, or self-protective — so that no choice reads as the obviously "correct" one. Choices should differ in what they cost and who they affect, not in whether they are smart or foolish. Cosmetic choices (no consequence) are permitted only where explicitly justified, per Scene_Template.md, and must be rare.

---

## Consequence Philosophy

Consequences must be proportionate, cumulative, and rarely catastrophic in isolation — the design intent is pressure that compounds over many choices, not single decisions that swing the game. Hidden consequences are permitted but must always have a prior, visible signal a careful player could have used to anticipate risk, in compliance with Engine_Core_Specification and Scene_Template.md fairness requirements. No consequence may be undone by spending currency after the fact.

---

## Economy Philosophy

Money is the spine of the real-world pressure system and must remain genuinely scarce throughout all four chapters — the player should never reach a comfortable financial buffer for more than a brief stretch. Spending money should almost always be a visible tradeoff against time, trust, or risk, never a free action. The economy is designed to make the player feel the same desperation driving Daniel's original decision to take the contract.

---

## Premium Philosophy

Premium currency exists exclusively to change *method* — unlocking an alternative approach to a Decision scene (faster, safer, better-connected) — and must never directly increase the probability of success to certainty or bypass a consequence outright. Every premium-currency interaction must have a free, slower, or riskier non-premium equivalent path available. Premium currency must never be the only way to access story content, characters, or endings.

---

## Time System

Time is tracked through a deadline-pressure variable (days remaining until funding/financial consequence) and a current-day counter, both at the Time category. Time pressure should tighten across the four chapters, not stay constant — later chapters should structurally allow less room for caution than earlier ones, reinforcing escalating stakes without requiring new mechanics.

---

## Knowledge System

Knowledge is tracked across historical, engineering/evidence, and map/site understanding sub-tracks, all within the engine's single Knowledge category. Each sub-track should be advanced primarily through Discovery and Information-purpose scenes, and should gate access to deeper Conflict, Character, and Consequence scenes later in the same or subsequent chapters. No Knowledge track should be advanceable through spending alone — investigation must require player choices, not just resources.

---

## Trust System

Trust is tracked per major character as Relationship-category variables. Trust should move primarily through Decision and Character-purpose scenes where Daniel chooses candor versus self-interest. Trust thresholds gate access to certain Knowledge, Discovery, and ending content per character, but no character's trust should be raisable purely through monetary spend — trust must always cost something relational (honesty, time, risk), never only money.

---

## Clue System

Clues are represented as a combination of Knowledge-variable increases and discrete StateFlags marking specific discoveries. Clues should be discoverable through multiple independent paths where possible (e.g., a clue reachable via the Archaeologist or via independent site investigation), so that no single missed scene permanently locks the player out of understanding the central mystery — though specific framing or interpretation of a clue may still vary by path taken.

---

## Mystery Design

The central mystery operates on two simultaneous layers: the historical fate of the caravan (designed to be resolvable with reasonable specificity by endgame) and the source of Daniel's impressions (designed to never be resolvable, by any combination of choices). Mystery pacing should reveal historical-layer answers steadily across all four chapters, while keeping the impression-source question's two interpretations equally supported at every checkpoint.

---

## Red Herring Design

Red herrings should redirect attention toward plausible but ultimately secondary threats (e.g., institutional/legal risk, competitive pressure from the Rival) so that the player's vigilance is engaged without it pointing at the true central tension. Red herrings must always resolve into something narratively real and consequential in their own right — never into a "nothing happened" reveal — so they never feel like wasted player effort.

---

## Failure Design

There are no premature game-ending failure states. Failure is represented as a harder, more constrained continuation: reduced trust, increased legal exposure, worse financial position, or lost evidence. Every failure state must remain narratively legible and must carry forward into later chapters and into ending eligibility, rather than being narratively erased or treated as a soft reset.

---

## Ending Design

Multiple endings are determined by final standing across financial outcome, relationship outcomes (particularly Mother and the Archaeologist or Local Guide), legal/heritage outcome, and how much historical truth was preserved versus lost. No ending may state or imply a definitive answer to whether Daniel's impressions were genuinely inherited memory or psychological strain; every ending must be writable as fully coherent under both interpretations.

---

## Replayability

Replayability is designed around variable-state divergence rather than branching scene structure — a second playthrough should feel meaningfully different because of which trust, knowledge, and risk thresholds were crossed, not because entirely different scenes were visited. This keeps production scope bounded while still rewarding replays with different endings and different character outcomes.

---

## Difficulty Philosophy

There is no skill-based difficulty in the traditional sense; difficulty is expressed entirely through resource scarcity and the tightness of tradeoffs offered at each Decision scene. The design should avoid ever giving the player a choice that is free of cost — perceived "easy mode" should not exist within a single playthrough's economy.

---

## Emotional Curve

The intended curve moves from quiet anxiety (Chapter 1) through escalating unease and competing loyalties (Chapter 2), into personal reckoning (Chapter 3), and finally into a tense convergence and irreversible commitment (Chapter 4). Each chapter should raise stakes on at least two of: financial pressure, relational complexity, legal/physical risk, or mystery intensity — never flattening into a plateau.

---

## Chapter Progression

Each chapter must end on a state that cannot be reversed by later player choices, ensuring that chapter transitions feel like real narrative commitments rather than checkpoints. Chapter-to-chapter, the player's standing (not their scene path) is what carries forward and determines available content.

---

## Character Progression

Characters other than Daniel do not gain new abilities, but their relationship to Daniel and their behavior toward him shift based on accumulated Trust and StateFlag outcomes. Each major character should have at least one chapter-level turning point where their relationship to Daniel measurably changes, consistent with their arc defined in Character_Bible.md.

---

## Risk Escalation

Legal Risk, Heritage Authority Attention, and Black Market Exposure should each escalate independently across the four chapters based on player choices, with no single chapter allowed to fully resolve any of these tracks. By Chapter 4, at least one of these tracks should be functionally unavoidable in some form, regardless of how cautiously the player has played, to preserve narrative tension into the climax.

---

## Discovery Flow

Discoveries should generally follow a three-step rhythm: a Discovery-purpose scene surfaces new evidence, an Information or Character-purpose scene contextualizes it, and a subsequent Decision-purpose scene forces the player to act on it. This rhythm should be used consistently enough that writers across chapters can rely on it as a structural default, while allowing variation where a scene's dramatic purpose calls for compression or expansion.

---

## Information Flow

Information should reach the player through multiple competing sources (Daniel's own assessment, the Archaeologist, the Local Guide, the Heritage Officer, family members) who do not always agree, so the player must weigh source reliability rather than receive a single authoritative narrator. No single character should function as an omniscient guide to the mystery.

---

## Player Agency

Agency is expressed through resource allocation and disclosure choices (who to tell what, when), not through dialogue-tree personality selection or combat-style decision-making. The player should feel their choices shape Daniel's situation and relationships meaningfully, even though Daniel's core personality and voice remain authored and consistent.

---

## Things This Game Must Never Become

- A game where premium currency guarantees any outcome.
- A game where any character, document, or system confirms the supernatural explanation as objectively true.
- A game with combat, action sequences, or twitch-skill mechanics.
- A game where money or trust can be infinitely farmed without narrative cost.
- A game that treats Khuzestan, Persian/Achaemenid history, or Iranian culture as exotic backdrop rather than grounded, researched setting.
- A game with a clean, universally "best" ending state.

---

## Production Risks

- Variable-state divergence without sufficient scene-level differentiation could make playthroughs feel mechanically different but narratively similar — chapter blueprints must specify enough distinct scene-level acknowledgment of state to avoid this.
- Maintaining strict ambiguity across many writers and many scenes over four chapters risks accidental drift toward confirming one interpretation; this requires ongoing editorial review against World_Bible.md's Rules of Ambiguity.
- Escalating risk tracks (Legal Risk, Heritage Attention, Black Market Exposure) across four chapters require careful tuning to avoid either trivializing risk or making it feel punitive/unfair.
- Multiple ending eligibility conditions across several variable tracks increase QA complexity; ending conditions must be explicitly documented and tested per ending before Chapter 4 is locked.

---

## Future Expansion

The variable and trust systems are designed to support additional post-ending or parallel content (e.g., epilogue material, additional caravan-route content) without requiring new core systems, provided any expansion strictly preserves the ambiguity policy and does not retroactively resolve the central mystery established across the four main chapters.
