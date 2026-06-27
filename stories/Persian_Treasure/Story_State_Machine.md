# Story State Machine: Persian Treasure

---

## Purpose

This document defines every major narrative state the game can be in, independent of any specific scene or chapter. Scenes change variables; variables change states; states determine what is currently true about the story at any given point in a playthrough. This document is the master continuity reference that all future Chapter blueprints, scenes, and characters must conform to — it exists to make contradictory future writing structurally difficult rather than merely discouraged.

---

## State Machine Philosophy

Narrative states are coarse-grained, durable facts about the story world — not moment-to-moment scene content. A state, once entered, remains true until an explicit, defined exit condition is met; states are never silently abandoned or reversed by scene-level prose. Multiple states from different categories are normally active simultaneously (e.g., Investigation and Legal states progress independently), and writers must check this document before introducing any scene that would imply a state change. States never resolve the central ambiguity of the story; any state touching Daniel's impressions must remain compatible with both the inherited-memory and psychological-strain interpretations, per World_Bible.md.

---

## Narrative State Rules

- A state may only be entered if its Entry Conditions are satisfied by current variable values and currently active states.
- A state may only be exited if its Exit Conditions are satisfied; states do not expire on their own or through the passage of chapters alone.
- A state's Allowed Previous States and Allowed Next States define the only legal transitions; any transition not listed is illegal by default.
- States within the same category are normally mutually exclusive at a given moment unless explicitly noted otherwise; states across different categories are independent and may overlap freely.
- No state may be defined, entered, or exited in a way that confirms or denies the supernatural interpretation of Daniel's impressions.
- States are referenced by ID in Chapter blueprints and scene Continuity sections, but this document never references specific scene IDs — it is scene-agnostic by design.

---

## State Categories

- Investigation
- Family
- Legal
- Financial
- Historical
- Psychological
- Social

---

## Investigation States

### INV-01: Site Assessed
- Name: Site Assessed
- Description: Daniel has performed an initial structural and historical assessment of the excavation site.
- Entry Conditions: var_engineering_assessment and var_evidence_progress both above their initial values
- Exit Conditions: Never exits; this state is foundational and remains true for the rest of the game
- Variables involved: var_engineering_assessment, var_evidence_progress
- Allowed previous states: None (entry-tier state)
- Allowed next states: INV-02
- Narrative meaning: Daniel has enough firsthand knowledge of the site to act as a credible assessor going forward
- Gameplay impact: Unlocks access to Discovery-purpose content gated on baseline site knowledge
- Writer notes: Do not write any scene assuming deeper site knowledge than this state implies until INV-02 is entered
- QA notes: Verify no scene references specific excavation findings before this state is confirmed entered

### INV-02: Artifact Found
- Name: Artifact Found
- Description: A physical artifact fragment connecting the site to the historical caravan has been discovered.
- Entry Conditions: INV-01 active; var_has_artifact_sample true
- Exit Conditions: Never exits once entered
- Variables involved: var_has_artifact_sample, var_evidence_progress, var_historical_knowledge
- Allowed previous states: INV-01
- Allowed next states: INV-03, HIST-01
- Narrative meaning: The excavation is confirmed to hold historically significant material, not just an engineering obstruction
- Gameplay impact: Unlocks Archaeologist-related content and Heritage/Legal escalation paths
- Writer notes: This state must be reachable through more than one investigative approach to avoid a single point of failure
- QA notes: Confirm var_has_artifact_sample cannot be set true without var_evidence_progress also increasing

### INV-03: Route Confirmed
- Name: Route Confirmed
- Description: The general path and approximate purpose of the historical caravan's route has been established through physical evidence.
- Entry Conditions: INV-02 active; var_map_knowledge and var_historical_knowledge above a moderate threshold
- Exit Conditions: Never exits once entered
- Variables involved: var_map_knowledge, var_historical_knowledge, var_evidence_progress
- Allowed previous states: INV-02
- Allowed next states: INV-04
- Narrative meaning: The historical mystery has moved from speculative to traceable
- Gameplay impact: Enables Chapter 2-level escalation content (Heritage scrutiny, Rival activity)
- Writer notes: Must be paired with at least one independent corroborating source (e.g. Archaeologist or physical record) before being treated as established fact in dialogue
- QA notes: Verify this state cannot be entered before INV-02

### INV-04: Caravan Fate Known
- Name: Caravan Fate Known
- Description: The historical cause and outcome of the caravan's disappearance has been fully resolved.
- Entry Conditions: INV-03 active; HIST-02 active
- Exit Conditions: Never exits once entered
- Variables involved: var_historical_knowledge, var_evidence_progress
- Allowed previous states: INV-03
- Allowed next states: None (terminal investigation state)
- Narrative meaning: The historical-layer mystery is resolved; the personal-impression-source mystery remains explicitly unresolved
- Gameplay impact: Required for reaching Chapter 4's Final Disclosure state and any ending
- Writer notes: Resolving this state must never require or imply resolution of the Psychological category ambiguity
- QA notes: Confirm no ending is reachable without this state active

---

## Family States

### FAM-01: Family Tension Hinted
- Name: Family Tension Hinted
- Description: Unexplained tension or evasiveness around the region has surfaced in contact with Mother and/or Father.
- Entry Conditions: flag_family_history_hinted true
- Exit Conditions: Never exits once entered
- Variables involved: flag_family_history_hinted, var_trust_mother, var_trust_father
- Allowed previous states: None (entry-tier state)
- Allowed next states: FAM-02
- Narrative meaning: There is more to Daniel's family history than he currently understands
- Gameplay impact: Establishes the family-history thread as a known open question for the player
- Writer notes: Must not reveal any specific content of the family history at this stage
- QA notes: Verify no scene before this state references specific family-history content

### FAM-02: Family Secret Opened
- Name: Family Secret Opened
- Description: Daniel has directly confronted Mother and/or Father, and a partial version of the withheld family history has been disclosed.
- Entry Conditions: FAM-01 active; var_trust_mother or var_trust_father above a defined confrontation threshold
- Exit Conditions: Never exits once entered
- Variables involved: var_trust_mother, var_trust_father, flag_family_history_revealed
- Allowed previous states: FAM-01
- Allowed next states: FAM-03
- Narrative meaning: Daniel now possesses a partial, possibly incomplete or differently-angled account of his family's connection to the region
- Gameplay impact: Recontextualizes prior impressions without confirming their source; unlocks Chapter 3-level Psychological state progression
- Writer notes: The disclosed account must remain ambiguous enough to support both interpretations of Daniel's impressions
- QA notes: Confirm flag_family_history_revealed cannot be set true without FAM-01 having been active first

### FAM-03: Family Outcome Settled
- Name: Family Outcome Settled
- Description: Daniel's relational standing with Mother and/or Father has reached its final state for the remainder of the story.
- Entry Conditions: FAM-02 active; Chapter 3 Irreversible Commitment reached
- Exit Conditions: Never exits once entered
- Variables involved: var_trust_mother, var_trust_father
- Allowed previous states: FAM-02
- Allowed next states: None (terminal family state)
- Narrative meaning: The family relationship thread is locked in, for better or worse, ahead of the climax
- Gameplay impact: Determines which ending categories involving family reconciliation or estrangement remain reachable
- Writer notes: This state must be reachable in multiple relational tones (positive, negative, mixed) without any tone being treated as definitively "correct"
- QA notes: Verify this state is entered before any Chapter 4 ending-resolution content

---

## Legal States

### LEG-01: Unauthorized Activity Known
- Name: Unauthorized Activity Known
- Description: Daniel is aware the excavation is legally unauthorized.
- Entry Conditions: flag_excavation_unauthorized_known true
- Exit Conditions: Never exits once entered
- Variables involved: flag_excavation_unauthorized_known
- Allowed previous states: None (entry-tier state; true from game start)
- Allowed next states: LEG-02
- Narrative meaning: Baseline legal risk is established from the outset of the story
- Gameplay impact: Underlies all subsequent Legal Risk escalation
- Writer notes: This state is active from the first scene; do not write Daniel as unaware of this fact at any point
- QA notes: Confirm this state is active in the initial save state for every playthrough

### LEG-02: Authorities Alerted
- Name: Authorities Alerted
- Description: The Heritage Protection Officer or another legal authority has become formally aware of the excavation.
- Entry Conditions: LEG-01 active; var_heritage_authority_attention above a defined formal-scrutiny threshold
- Exit Conditions: Never exits once entered
- Variables involved: var_heritage_authority_attention, var_legal_risk
- Allowed previous states: LEG-01
- Allowed next states: LEG-03
- Narrative meaning: The excavation's legal risk has moved from latent to active
- Gameplay impact: Unlocks Heritage Officer cooperation/obstruction branches; raises stakes on all subsequent Decision content
- Writer notes: This state must be reachable through more than one path (direct disclosure, discovery by the officer independently, or escalation via another character)
- QA notes: Verify var_legal_risk increases whenever this state is entered, consistent with Variable-State Relationship rules below

### LEG-03: Legal Outcome Pending
- Name: Legal Outcome Pending
- Description: The Heritage/legal thread has reached a point where its eventual resolution is determined but not yet finalized.
- Entry Conditions: LEG-02 active; Chapter 3 Irreversible Commitment reached
- Exit Conditions: Resolved into LEG-04 at Chapter 4's Final Disclosure
- Variables involved: var_legal_risk, var_heritage_authority_attention
- Allowed previous states: LEG-02
- Allowed next states: LEG-04
- Narrative meaning: Daniel's legal fate is now substantially determined by accumulated risk and disclosure choices, awaiting final resolution
- Gameplay impact: Constrains which Chapter 4 disclosure options remain available
- Writer notes: Do not allow any Chapter 3 scene to fully resolve legal outcome ahead of Chapter 4
- QA notes: Confirm LEG-03 cannot be skipped en route to LEG-04

### LEG-04: Legal Outcome Resolved
- Name: Legal Outcome Resolved
- Description: Daniel's final legal standing is locked in as part of the ending.
- Entry Conditions: LEG-03 active; Final Disclosure state entered
- Exit Conditions: Never exits once entered
- Variables involved: var_legal_risk, var_heritage_authority_attention
- Allowed previous states: LEG-03
- Allowed next states: None (terminal legal state)
- Narrative meaning: The legal thread's outcome is part of the locked ending
- Gameplay impact: Feeds directly into Ending Locked state
- Writer notes: Must support a range of outcomes (no consequence, formal sanction, negotiated settlement) without any being a forced default
- QA notes: Verify every ending has a corresponding LEG-04 value consistent with its narrative description

---

## Financial States

### FIN-01: Contract Accepted
- Name: Contract Accepted
- Description: Daniel has formally accepted the excavation consulting contract.
- Entry Conditions: True from game start
- Exit Conditions: Never exits once entered
- Variables involved: var_money, var_debt_pressure
- Allowed previous states: None (entry-tier state)
- Allowed next states: FIN-02
- Narrative meaning: The financial premise of the entire story is established
- Gameplay impact: Establishes baseline Resource scarcity for all subsequent Decision scenes
- Writer notes: Every subsequent scene must treat this as settled fact; do not re-litigate whether Daniel accepted the contract
- QA notes: Confirm active in the initial save state for every playthrough

### FIN-02: Excavation Started
- Name: Excavation Started
- Description: Active excavation work has begun at the site under Daniel's involvement.
- Entry Conditions: FIN-01 active; var_excavation_progress above its initial value
- Exit Conditions: Never exits once entered
- Variables involved: var_excavation_progress, var_money
- Allowed previous states: FIN-01
- Allowed next states: FIN-03
- Narrative meaning: The excavation is no longer hypothetical; resources are actively being spent and consequences are now live
- Gameplay impact: Unlocks Discovery and Investigation-category state progression
- Writer notes: Pair with at least one tangible cost (time, money, or risk) to keep scarcity meaningful
- QA notes: Verify var_excavation_progress cannot increase before this state is entered

### FIN-03: Funding Crisis Active
- Name: Funding Crisis Active
- Description: The funding deadline has tightened to the point that further delay carries severe consequence.
- Entry Conditions: FIN-02 active; var_days_remaining below a defined critical threshold
- Exit Conditions: Resolved into FIN-04 at the Final Disclosure state
- Variables involved: var_days_remaining, var_money, var_debt_pressure
- Allowed previous states: FIN-02
- Allowed next states: FIN-04
- Narrative meaning: Time pressure has become the dominant constraint on Daniel's remaining choices
- Gameplay impact: Narrows available options in Chapter 4 Decision scenes; raises the cost of caution
- Writer notes: Must be reachable regardless of how cautiously the player has played, per Game_Design_Document.md Risk Escalation
- QA notes: Confirm this state is active before Chapter 4's Final Disclosure state can be entered

### FIN-04: Financial Outcome Resolved
- Name: Financial Outcome Resolved
- Description: Daniel's final financial standing is locked in as part of the ending.
- Entry Conditions: FIN-03 active; Final Disclosure state entered
- Exit Conditions: Never exits once entered
- Variables involved: var_money, var_debt_pressure
- Allowed previous states: FIN-03
- Allowed next states: None (terminal financial state)
- Narrative meaning: The financial thread's outcome is part of the locked ending
- Gameplay impact: Feeds directly into Ending Locked state
- Writer notes: Must support a meaningful range of outcomes from ruin to relief, none of which is mechanically guaranteed
- QA notes: Verify every ending has a corresponding FIN-04 value consistent with its narrative description

---

## Historical States

### HIST-01: Historical Interest Confirmed
- Name: Historical Interest Confirmed
- Description: A credible, legitimate historical/academic perspective (the Archaeologist) has confirmed the site's significance.
- Entry Conditions: INV-02 active; flag_met_archaeologist true
- Exit Conditions: Never exits once entered
- Variables involved: var_trust_archaeologist, var_historical_knowledge
- Allowed previous states: INV-02
- Allowed next states: HIST-02
- Narrative meaning: The historical mystery now has institutional/academic legitimacy, not just Daniel's personal interpretation
- Gameplay impact: Unlocks deeper Knowledge-track content gated on expert corroboration
- Writer notes: The Archaeologist's confirmation must remain strictly historical/material in nature, never validating Daniel's impressions directly
- QA notes: Confirm this state cannot be entered without flag_met_archaeologist true

### HIST-02: Caravan Cause Identified
- Name: Caravan Cause Identified
- Description: The specific cause of the caravan's disappearance has been identified through physical/historical evidence.
- Entry Conditions: HIST-01 active; INV-03 active
- Exit Conditions: Never exits once entered
- Variables involved: var_historical_knowledge, var_evidence_progress
- Allowed previous states: HIST-01
- Allowed next states: None (feeds INV-04 directly)
- Narrative meaning: The historical mystery's central question — what happened to the caravan — is materially answered
- Gameplay impact: Required precondition for INV-04 (Caravan Fate Known)
- Writer notes: The identified cause must be grounded in plausible historical/environmental/political circumstance per World_Bible.md, never supernatural
- QA notes: Verify INV-04 cannot be entered without this state active first

---

## Psychological States

### PSY-01: First Impression
- Name: First Impression
- Description: Daniel experiences his first vivid, specific impression of the ancient caravan.
- Entry Conditions: flag_first_vision_experienced true; var_fatigue or var_stress above a defined elevated threshold
- Exit Conditions: Never exits once entered
- Variables involved: var_vision_intensity, var_vision_doubt, var_fatigue, flag_first_vision_experienced
- Allowed previous states: None (entry-tier state within this category)
- Allowed next states: PSY-02
- Narrative meaning: The personal/ambiguous mystery thread begins
- Gameplay impact: Establishes the baseline for all subsequent Vision Intensity and Vision Doubt progression
- Writer notes: Must occur under conditions that independently and fully explain the impression through fatigue/stress alone, per World_Bible.md
- QA notes: Confirm var_fatigue or var_stress was elevated immediately prior to this state's entry in all playthroughs

### PSY-02: Impressions Escalating
- Name: Impressions Escalating
- Description: Impressions recur with increasing specificity, tracking discoveries at the excavation site.
- Entry Conditions: PSY-01 active; var_vision_intensity above a moderate threshold
- Exit Conditions: Never exits once entered
- Variables involved: var_vision_intensity, var_vision_doubt
- Allowed previous states: PSY-01
- Allowed next states: PSY-03
- Narrative meaning: The ambiguity is sustained at increasing intensity rather than resolved
- Gameplay impact: Gates access to Chapter 2–3 level Emotion-purpose content
- Writer notes: Each escalation must be paired with a concurrent investigative or personal-knowledge gain that offers a mundane explanation, per Mystery Escalation in Story_Map.md
- QA notes: Verify var_vision_doubt never collapses to a fixed extreme (fully believed or fully disbelieved) before Chapter 4

### PSY-03: Impressions Intersect Personal History
- Name: Impressions Intersect Personal History
- Description: An impression directly intersects with content revealed through the Family Secret Opened state, deepening but not resolving the ambiguity.
- Entry Conditions: PSY-02 active; FAM-02 active
- Exit Conditions: Never exits once entered
- Variables involved: var_vision_intensity, var_vision_doubt
- Allowed previous states: PSY-02
- Allowed next states: PSY-04
- Narrative meaning: The personal and historical mystery threads visibly converge in Daniel's experience
- Gameplay impact: Required precondition for the climactic Chapter 4 impression
- Writer notes: This intersection must still permit a fully mundane reading (e.g., suggestibility following the family disclosure) alongside the inherited-memory reading
- QA notes: Confirm this state cannot be entered before FAM-02

### PSY-04: Ambiguity Sustained at Climax
- Name: Ambiguity Sustained at Climax
- Description: Daniel's final, climactic impression occurs at the same moment as the caravan's historical resolution, with the ambiguity fully intact.
- Entry Conditions: PSY-03 active; INV-04 active
- Exit Conditions: Never exits; this state persists through Ending Locked
- Variables involved: var_vision_intensity, var_vision_doubt
- Allowed previous states: PSY-03
- Allowed next states: None (terminal psychological state)
- Narrative meaning: The story's defining ambiguity is preserved at its highest emotional stakes through to the ending
- Gameplay impact: No ending may be reached without this state active; it is a hard gate on Ending Locked
- Writer notes: No scene, document, or character line associated with this state may tip the ambiguity decisively in either direction
- QA notes: This is the single highest-priority QA gate in the entire package; every ending must be checked against this state's narrative meaning before release

---

## Social States

### SOC-01: Site Confirmed
- Name: Site Confirmed
- Description: The excavation site's physical conditions and immediate community context are established as common knowledge among recurring local characters.
- Entry Conditions: flag_met_local_guide true; var_map_knowledge above its initial value
- Exit Conditions: Never exits once entered
- Variables involved: var_map_knowledge, var_trust_local_guide
- Allowed previous states: None (entry-tier state within this category)
- Allowed next states: SOC-02
- Narrative meaning: Daniel is no longer an unknown outsider at the site; his presence is socially established
- Gameplay impact: Unlocks community-gated Discovery and Character content
- Writer notes: This state does not imply trust, only awareness — trust is tracked separately via var_trust_local_guide
- QA notes: Confirm flag_met_local_guide is true before any scene assumes community familiarity with Daniel

### SOC-02: Rival Active
- Name: Rival Active
- Description: The Rival Treasure Hunter is actively and visibly competing for access to the excavation's findings.
- Entry Conditions: SOC-01 active; INV-02 active
- Exit Conditions: Never exits once entered
- Variables involved: var_evidence_progress, var_reputation
- Allowed previous states: SOC-01
- Allowed next states: SOC-03
- Narrative meaning: External competitive pressure is now a live narrative force, not background risk
- Gameplay impact: Introduces time-sensitive Decision content and potential Conflict-purpose escalation
- Writer notes: The Rival's activity must escalate independently of player choice to some degree, per Game_Design_Document.md Risk Escalation
- QA notes: Confirm this state cannot be entered before INV-02

### SOC-03: Social Outcome Settled
- Name: Social Outcome Settled
- Description: Daniel's professional reputation and standing with the broader community/competitive landscape reach their final state.
- Entry Conditions: SOC-02 active; Final Disclosure state entered
- Exit Conditions: Never exits once entered
- Variables involved: var_reputation
- Allowed previous states: SOC-02
- Allowed next states: None (terminal social state)
- Narrative meaning: The social/professional thread's outcome is part of the locked ending
- Gameplay impact: Feeds directly into Ending Locked state
- Writer notes: Must support outcomes ranging from professional vindication to discredit, none of which is a forced default
- QA notes: Verify every ending has a corresponding SOC-03 value consistent with its narrative description

---

## Cross-Category Convergence States

### CONV-01: Final Disclosure
- Name: Final Disclosure
- Description: Daniel makes his final, irreversible decision on what to disclose, to whom, and at what cost.
- Entry Conditions: INV-04 active; FAM-03 reachable concurrently; LEG-03 active; FIN-03 active; PSY-04 active
- Exit Conditions: Immediately resolves into CONV-02 (Ending Locked)
- Variables involved: All Resource, Social, Legal, Relationship, and Psychological variables at their pre-ending values
- Allowed previous states: INV-04, LEG-03, FIN-03, PSY-04 (joint precondition)
- Allowed next states: CONV-02
- Narrative meaning: The single decisive narrative moment that determines which ending is reached
- Gameplay impact: The last Decision-purpose content in the game; no further state may change after this except through its direct resolution
- Writer notes: This must be written as one clearly identifiable decisive moment, not a diffuse series of small choices, to preserve its weight as the story's final commitment
- QA notes: Verify all five joint preconditions are independently satisfiable without forcing a single linear path to this state

### CONV-02: Ending Locked
- Name: Ending Locked
- Description: The final ending category is determined and fixed; the playthrough is narratively complete.
- Entry Conditions: CONV-01 resolved
- Exit Conditions: Terminal; never exits
- Variables involved: All variables at their final values
- Allowed previous states: CONV-01
- Allowed next states: None (terminal state for the entire state machine)
- Narrative meaning: The playthrough's complete story is now fixed and legible as a coherent whole
- Gameplay impact: Triggers ending-specific content per Story_Map.md Ending Structure
- Writer notes: Confirm the resolved combination of LEG-04, FIN-04, FAM-03, SOC-03, and PSY-04 values matches one of the defined ending categories in Story_Map.md
- QA notes: This is the final QA gate; no playthrough may reach this state without every terminal state in every category having a defined, consistent value

---

## Global State Flow

The game progresses through five broad waves, corresponding loosely to the four chapters plus their convergence:

1. **Foundation** (Chapter 1): FIN-01 → FIN-02; LEG-01 (already active) → LEG-02 begins; INV-01 → INV-02; FAM-01 begins; SOC-01 begins; PSY-01 entered.
2. **Escalation** (Chapter 2): INV-02 → INV-03; HIST-01 entered; LEG-02 solidifies; SOC-02 entered; PSY-01 → PSY-02.
3. **Reckoning** (Chapter 3): FAM-01 → FAM-02; HIST-02 entered; LEG-02 → LEG-03; FIN-02 → FIN-03; PSY-02 → PSY-03.
4. **Convergence** (Chapter 4, pre-climax): INV-03 → INV-04 (via HIST-02); FAM-02 → FAM-03; PSY-03 → PSY-04.
5. **Resolution** (Chapter 4, climax): CONV-01 → CONV-02, drawing on the terminal state of every category simultaneously.

At every wave boundary, all category states active so far remain active; no wave transition retroactively closes a category's progress. The Psychological category is the only category whose terminal state (PSY-04) is a hard joint precondition for the final convergence, reflecting its status as the story's central, unresolved thread.

---

## Mandatory States

The following states are required to exist, in this or a future revision, and must each map to exactly one state ID defined above:

| Required State | Mapped State ID |
|---|---|
| Contract Accepted | FIN-01 |
| Excavation Started | FIN-02 |
| First Impression | PSY-01 |
| Site Confirmed | SOC-01 |
| Historical Interest Confirmed | HIST-01 |
| Authorities Alerted | LEG-02 |
| Rival Active | SOC-02 |
| Family Secret Opened | FAM-02 |
| Route Confirmed | INV-03 |
| Caravan Fate Known | INV-04 |
| Final Disclosure | CONV-01 |
| Ending Locked | CONV-02 |

---

## State Transition Rules

- A state transition is legal only if the destination state's Entry Conditions are met and the destination state appears in the current state's Allowed Next States.
- Transitions are one-directional within a category; no state may transition back into an earlier state in its own category once exited.
- Cross-category convergence states (CONV-01, CONV-02) require simultaneous satisfaction of joint preconditions across multiple categories, not sequential satisfaction.
- A category may have at most one active "current" state per playthrough at any given time, except where a state is explicitly marked as non-exiting (in which case it remains true alongside its successor).

---

## Illegal Transitions

- Entering any Historical or Investigation terminal state (INV-04, HIST-02) before the corresponding non-terminal states in the same category.
- Entering CONV-01 without all five joint preconditions (INV-04, FAM-03 reachability, LEG-03, FIN-03, PSY-04) satisfied.
- Entering PSY-04 without INV-04 active.
- Re-entering any state marked terminal within its category.
- Any transition that would require a state's Entry Conditions to be satisfied through variable values alone without the prerequisite state being logically true first (e.g., raising var_historical_knowledge high enough to "look like" HIST-02 without HIST-01 having occurred).

---

## Soft Locks

A soft lock occurs when a category's progress stalls because its current state's Exit Conditions cannot be met given the player's accumulated variable standing (e.g., Trust too low to ever reach FAM-02's confrontation threshold). Soft locks must be designed with a recovery path at the chapter level (see State Recovery Rules) rather than treated as failure states; per Game_Design_Document.md Failure Design, no narrative state may produce a premature game-ending condition.

---

## Hard Locks

A hard lock would occur only if a Cross-Category Convergence state's joint preconditions became permanently unreachable. This must never be allowed to occur by design: every category's terminal pre-convergence state (LEG-03, FIN-03, FAM-03's reachability, INV-04, PSY-04) must remain reachable from any combination of prior player choices, even in worst-case variable standing, by Chapter 4. Chapter blueprints must include a guaranteed-reachable path to each of these states regardless of accumulated player failure.

---

## State Recovery Rules

When a category's progress stalls (soft lock), the next chapter blueprint must provide an alternate, lower-trust or higher-cost path to the same next state, consistent with Game_Design_Document.md's Failure Design (harder continuation, never a dead end). Recovery paths must carry a worse but plausible cost (e.g., reduced Trust ceiling, increased Legal Risk) rather than being free equivalents of the missed path.

---

## Branch Merge Rules

Divergent variable standing entering a chapter must merge back into the same set of narrative states by the chapter's end, per Story_Map.md's variable-state-divergence philosophy — chapters do not fork into separate state machines. A merge is valid only if every divergent path satisfies the next state's Entry Conditions by the chapter's defined Irreversible Commitment point, even if the values used to satisfy them differ (e.g., reaching LEG-02 via direct disclosure versus via independent discovery by the Heritage Officer).

---

## Variable-State Relationship

Variables are continuous or discrete data; states are the discrete, named narrative facts derived from thresholds and combinations of variables and prior states. A variable crossing a threshold does not itself constitute a state change — it only makes a state's Entry Conditions satisfiable. The actual state transition still requires the corresponding scene-level narrative event to occur, ensuring that no state is ever "accidentally" entered purely through numeric drift (e.g., var_stress drifting upward over many unrelated scenes must not silently trigger PSY-01 without a dedicated scene enacting that transition). This separation prevents contradictory story progression: variables may fluctuate continuously, but the discrete states they unlock only become true at an authored narrative moment, keeping the story's logical sequence fully writer-controlled even as numeric values vary across divergent playthroughs.
