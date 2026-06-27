# Narrative Event Catalog: Persian Treasure

---

## Purpose

This document defines every major narrative event that triggers a state transition in Persian Treasure. It is the bridge between Story_State_Machine.md and future Chapter blueprints and scenes. Scenes do not advance the story by loose implication — a scene triggers one or more defined Narrative Events, and those events are what update narrative states. This document exists so that no state transition is ever hidden inside prose; every transition must be traceable to a named, catalogued event.

---

## Event Philosophy

A Narrative Event is the explicit, named cause of a state transition — the thing a scene does, not the scene itself. Events are deliberately coarse-grained: many scenes may build toward an event, but the event itself fires once, at a specific authored moment, consistent with Story_State_Machine.md's Variable-State Relationship principle that numeric drift alone must never silently trigger a state change. Every event in this catalog must trace to exactly one or more states in Story_State_Machine.md, and no event may be invented at the scene level without first being added here.

---

## Event Rules

- Every event must specify the state(s) it transitions, consistent with that state's Entry Conditions in Story_State_Machine.md.
- An event may only fire if its Required Active States and Required Variables/Flags are satisfied at the time a scene attempts to trigger it.
- An event fires at most once per category-state transition per playthrough, except where explicitly marked as repeatable.
- No event description, trigger, or consequence may confirm or deny the supernatural interpretation of Daniel's impressions.
- Numeric thresholds referenced here must already exist as defined min/max ranges in variables.json; this document does not invent new thresholds, only refers to qualitative bands (e.g. "elevated," "moderate") consistent with existing variable ranges.
- Chapter blueprints and scenes must reference events by Event ID when describing what a scene accomplishes, rather than describing state changes in free narrative terms.

---

## Event Categories

- Financial
- Investigation
- Legal
- Family
- Historical
- Psychological
- Social
- Convergence
- Ending

---

## Financial Events

### EVT-FIN-01: Contract Accepted
- Event Name: Contract Accepted
- Category: Financial
- Description: Daniel formally commits to the unauthorized excavation consulting contract.
- Triggered By: The opening scene establishing Daniel's financial situation and the contract's terms
- Required Active States: None (game-start event)
- Required Variables / Flags: None
- State Changes: Enters FIN-01 (Contract Accepted)
- Variables Usually Affected: var_money, var_debt_pressure
- Narrative Meaning: Establishes the financial premise that drives the entire story
- Gameplay Impact: Unlocks all subsequent Financial category progression
- Writer Notes: This event must occur in the first scene of the game; no prior scene may exist
- QA Notes: Confirm FIN-01 is active in every save state from the first checkpoint onward

### EVT-FIN-02: Excavation Started
- Event Name: Excavation Started
- Category: Financial
- Description: Daniel begins active excavation work at the site.
- Triggered By: Daniel's first hands-on involvement with the dig after arriving on-site
- Required Active States: FIN-01
- Required Variables / Flags: None
- State Changes: Enters FIN-02 (Excavation Started)
- Variables Usually Affected: var_excavation_progress, var_money
- Narrative Meaning: The excavation moves from hypothetical to active and resource-consuming
- Gameplay Impact: Unlocks Investigation category progression
- Writer Notes: Pair with a visible cost (time, money, or fatigue) to keep scarcity meaningful
- QA Notes: Verify var_excavation_progress cannot increase before this event fires

### EVT-FIN-03: Funding Crisis Active
- Event Name: Funding Crisis Active
- Category: Financial
- Description: The funding deadline tightens to a critical point, narrowing Daniel's remaining options.
- Triggered By: A scene in which backers, time pressure, or financial review forces an acknowledgment that delay is no longer affordable
- Required Active States: FIN-02
- Required Variables / Flags: var_days_remaining at a low band consistent with variables.json's defined range
- State Changes: Enters FIN-03 (Funding Crisis Active)
- Variables Usually Affected: var_days_remaining, var_money, var_debt_pressure
- Narrative Meaning: Time pressure becomes the dominant constraint on Daniel's choices
- Gameplay Impact: Narrows available Decision options in later chapters
- Writer Notes: Must be reachable regardless of how cautiously the player has played, per Game_Design_Document.md Risk Escalation
- QA Notes: Confirm this event is reachable from every divergent financial path entering Chapter 4

### EVT-FIN-04: Financial Outcome Resolved
- Event Name: Financial Outcome Resolved
- Category: Financial
- Description: Daniel's final financial standing is fixed as part of the ending.
- Triggered By: The Final Disclosure event
- Required Active States: FIN-03
- Required Variables / Flags: None beyond FIN-03's own preconditions
- State Changes: Enters FIN-04 (Financial Outcome Resolved)
- Variables Usually Affected: var_money, var_debt_pressure
- Narrative Meaning: The financial thread's outcome becomes part of the locked ending
- Gameplay Impact: Feeds Ending Locked
- Writer Notes: Must support outcomes ranging from ruin to relief, none of which is mechanically forced
- QA Notes: Verify every ending maps to a specific, consistent FIN-04 value

---

## Investigation Events

### EVT-INV-01: First Site Assessment
- Event Name: First Site Assessment
- Category: Investigation
- Description: Daniel performs his first structural and historical assessment of the excavation site.
- Triggered By: Daniel's initial hands-on inspection of the excavation pit
- Required Active States: FIN-02
- Required Variables / Flags: None
- State Changes: Enters INV-01 (Site Assessed)
- Variables Usually Affected: var_engineering_assessment, var_evidence_progress
- Narrative Meaning: Daniel establishes firsthand, credible knowledge of the site
- Gameplay Impact: Unlocks baseline Discovery-purpose content
- Writer Notes: Do not allow any prior scene to assume deeper site knowledge than this event grants
- QA Notes: Confirm var_engineering_assessment and var_evidence_progress both rise at this event

### EVT-INV-02: First Artifact Found
- Event Name: First Artifact Found
- Category: Investigation
- Description: Daniel discovers a physical artifact fragment connecting the site to the historical caravan.
- Triggered By: A Discovery-purpose scene during excavation work
- Required Active States: INV-01
- Required Variables / Flags: None
- State Changes: Enters INV-02 (Artifact Found)
- Variables Usually Affected: var_has_artifact_sample, var_evidence_progress, var_historical_knowledge
- Narrative Meaning: Confirms the site holds historically significant material
- Gameplay Impact: Unlocks Archaeologist, Heritage, and Black Market-adjacent content
- Writer Notes: This event must be reachable through more than one investigative approach to avoid a single point of failure
- QA Notes: Confirm var_has_artifact_sample cannot become true without this event having fired

### EVT-INV-03: Route Confirmed
- Event Name: Route Confirmed
- Category: Investigation
- Description: The general path and approximate purpose of the caravan's route is established through physical evidence.
- Triggered By: A Discovery or Information-purpose scene synthesizing multiple findings, typically corroborated by the Archaeologist
- Required Active States: INV-02, HIST-01
- Required Variables / Flags: var_map_knowledge and var_historical_knowledge at a moderate band consistent with variables.json
- State Changes: Enters INV-03 (Route Confirmed)
- Variables Usually Affected: var_map_knowledge, var_historical_knowledge, var_evidence_progress
- Narrative Meaning: The historical mystery moves from speculative to traceable
- Gameplay Impact: Enables Chapter 2-level escalation (Heritage scrutiny, Rival activity)
- Writer Notes: Pair with at least one independent corroborating source before treating the route as established fact in dialogue
- QA Notes: Verify this event cannot fire before EVT-INV-02 and EVT-HIST-01

### EVT-INV-04: Caravan Fate Known
- Event Name: Caravan Fate Known
- Category: Investigation
- Description: The full historical fate of the caravan is resolved.
- Triggered By: The culminating Discovery/Information scene of Chapter 4's historical thread
- Required Active States: INV-03, HIST-02
- Required Variables / Flags: None beyond prerequisite states
- State Changes: Enters INV-04 (Caravan Fate Known)
- Variables Usually Affected: var_historical_knowledge, var_evidence_progress
- Narrative Meaning: The historical-layer mystery is fully answered
- Gameplay Impact: Required precondition for Final Disclosure and every ending
- Writer Notes: Resolving this event must never require or imply resolution of the Psychological category ambiguity
- QA Notes: Confirm no ending is reachable without this event having fired

---

## Legal Events

### EVT-LEG-01: Authorities Alerted
- Event Name: Authorities Alerted
- Category: Legal
- Description: The Heritage Protection Officer or another legal authority becomes formally aware of the excavation.
- Triggered By: Either Daniel's disclosure to the Heritage Officer, independent discovery by the officer, or escalation via another character
- Required Active States: LEG-01 (active from game start)
- Required Variables / Flags: var_heritage_authority_attention at a formal-scrutiny band consistent with variables.json
- State Changes: Enters LEG-02 (Authorities Alerted)
- Variables Usually Affected: var_heritage_authority_attention, var_legal_risk
- Narrative Meaning: Legal risk moves from latent to active
- Gameplay Impact: Unlocks Heritage Officer cooperation/obstruction branches
- Writer Notes: Must be reachable through more than one path (direct disclosure, independent discovery, third-party escalation)
- QA Notes: Verify var_legal_risk increases whenever this event fires

### EVT-LEG-02: Legal Outcome Pending
- Event Name: Legal Outcome Pending
- Category: Legal
- Description: The legal/heritage thread reaches a point where its eventual resolution is determined but not yet finalized.
- Triggered By: Chapter 3's Irreversible Commitment scene
- Required Active States: LEG-02
- Required Variables / Flags: None beyond LEG-02's own preconditions
- State Changes: Enters LEG-03 (Legal Outcome Pending)
- Variables Usually Affected: var_legal_risk, var_heritage_authority_attention
- Narrative Meaning: Daniel's legal fate is substantially determined, awaiting final resolution
- Gameplay Impact: Constrains available Chapter 4 disclosure options
- Writer Notes: Do not allow any Chapter 3 scene to fully resolve legal outcome ahead of Chapter 4
- QA Notes: Confirm this event cannot be skipped en route to EVT-LEG-03

### EVT-LEG-03: Legal Outcome Resolved
- Event Name: Legal Outcome Resolved
- Category: Legal
- Description: Daniel's final legal standing is fixed as part of the ending.
- Triggered By: The Final Disclosure event
- Required Active States: LEG-03
- Required Variables / Flags: None beyond LEG-03's own preconditions
- State Changes: Enters LEG-04 (Legal Outcome Resolved)
- Variables Usually Affected: var_legal_risk, var_heritage_authority_attention
- Narrative Meaning: The legal thread's outcome becomes part of the locked ending
- Gameplay Impact: Feeds Ending Locked
- Writer Notes: Must support a range of outcomes (no consequence, formal sanction, negotiated settlement)
- QA Notes: Verify every ending maps to a specific, consistent LEG-04 value

---

## Family Events

### EVT-FAM-01: Family Tension Hinted
- Event Name: Family Tension Hinted
- Category: Family
- Description: Unexplained tension or evasiveness around the region surfaces in contact with Mother and/or Father.
- Triggered By: A Character-purpose scene featuring remote contact with Mother (e.g. a phone call)
- Required Active States: None (entry-tier event within this category)
- Required Variables / Flags: None
- State Changes: Enters FAM-01 (Family Tension Hinted); sets flag_family_history_hinted true
- Variables Usually Affected: flag_family_history_hinted, var_trust_mother
- Narrative Meaning: Establishes that more exists in Daniel's family history than he currently understands
- Gameplay Impact: Establishes the family-history thread as a known open question for the player
- Writer Notes: Must not reveal any specific content of the family history at this stage
- QA Notes: Verify no scene before this event references specific family-history content

### EVT-FAM-02: Family Secret Opened
- Event Name: Family Secret Opened
- Category: Family
- Description: Daniel directly confronts Mother and/or Father, and a partial version of the withheld family history is disclosed.
- Triggered By: Chapter 3's confrontation scene
- Required Active States: FAM-01
- Required Variables / Flags: var_trust_mother or var_trust_father at a confrontation-ready band consistent with variables.json
- State Changes: Enters FAM-02 (Family Secret Opened); sets flag_family_history_revealed true
- Variables Usually Affected: var_trust_mother, var_trust_father, flag_family_history_revealed
- Narrative Meaning: Daniel gains a partial, possibly incomplete account of his family's connection to the region
- Gameplay Impact: Recontextualizes prior impressions; unlocks PSY-03 progression
- Writer Notes: The disclosed account must remain ambiguous enough to support both interpretations of Daniel's impressions
- QA Notes: Confirm flag_family_history_revealed cannot be set true without EVT-FAM-01 having fired first

### EVT-FAM-03: Family Outcome Settled
- Event Name: Family Outcome Settled
- Category: Family
- Description: Daniel's relational standing with Mother and/or Father reaches its final state.
- Triggered By: Chapter 3's Irreversible Commitment scene
- Required Active States: FAM-02
- Required Variables / Flags: None beyond FAM-02's own preconditions
- State Changes: Enters FAM-03 (Family Outcome Settled)
- Variables Usually Affected: var_trust_mother, var_trust_father
- Narrative Meaning: The family relationship thread is locked in ahead of the climax
- Gameplay Impact: Determines which ending categories involving family reconciliation or estrangement remain reachable
- Writer Notes: Must be reachable in multiple relational tones without any being treated as definitively correct
- QA Notes: Verify this event fires before any Chapter 4 ending-resolution content

---

## Historical Events

### EVT-HIST-01: Historical Interest Confirmed
- Event Name: Historical Interest Confirmed
- Category: Historical
- Description: A credible, legitimate academic perspective (the Archaeologist) confirms the site's historical significance.
- Triggered By: A Character-purpose scene introducing the Archaeologist's assessment of the find
- Required Active States: INV-02
- Required Variables / Flags: flag_met_archaeologist true
- State Changes: Enters HIST-01 (Historical Interest Confirmed)
- Variables Usually Affected: var_trust_archaeologist, var_historical_knowledge
- Narrative Meaning: The historical mystery gains institutional/academic legitimacy
- Gameplay Impact: Unlocks deeper Knowledge-track content gated on expert corroboration
- Writer Notes: The Archaeologist's confirmation must remain strictly historical/material, never validating Daniel's impressions directly
- QA Notes: Confirm this event cannot fire without flag_met_archaeologist true

### EVT-HIST-02: Caravan Cause Identified
- Event Name: Caravan Cause Identified
- Category: Historical
- Description: The specific cause of the caravan's disappearance is identified through physical/historical evidence.
- Triggered By: Chapter 3's culminating historical-discovery scene
- Required Active States: HIST-01, INV-03
- Required Variables / Flags: None beyond prerequisite states
- State Changes: Enters HIST-02 (Caravan Cause Identified)
- Variables Usually Affected: var_historical_knowledge, var_evidence_progress
- Narrative Meaning: The historical mystery's central question is materially answered
- Gameplay Impact: Required precondition for EVT-INV-04
- Writer Notes: The identified cause must be grounded in plausible historical/environmental/political circumstance, never supernatural
- QA Notes: Verify EVT-INV-04 cannot fire without this event having fired first

---

## Psychological Events

### EVT-PSY-01: First Impression Experienced
- Event Name: First Impression Experienced
- Category: Psychological
- Description: Daniel experiences his first vivid, specific impression of the ancient caravan.
- Triggered By: An Emotion-purpose scene occurring under conditions of elevated fatigue or stress, late in Chapter 1
- Required Active States: None (entry-tier event within this category)
- Required Variables / Flags: var_fatigue or var_stress at an elevated band consistent with variables.json
- State Changes: Enters PSY-01 (First Impression); sets flag_first_vision_experienced true
- Variables Usually Affected: var_vision_intensity, var_vision_doubt, var_fatigue, flag_first_vision_experienced
- Narrative Meaning: Begins the personal/ambiguous mystery thread
- Gameplay Impact: Establishes the baseline for all subsequent Vision Intensity and Vision Doubt progression
- Writer Notes: Must occur under conditions that independently and fully explain the impression through fatigue/stress alone
- QA Notes: Confirm var_fatigue or var_stress was elevated immediately prior to this event in all playthroughs

### EVT-PSY-02: Impressions Escalating
- Event Name: Impressions Escalating
- Category: Psychological
- Description: Impressions recur with increasing specificity, tracking discoveries at the excavation site.
- Triggered By: A recurring Emotion-purpose scene pattern across Chapter 2, each instance paired with a concurrent investigative gain
- Required Active States: PSY-01
- Required Variables / Flags: var_vision_intensity at a moderate band consistent with variables.json
- State Changes: Enters PSY-02 (Impressions Escalating)
- Variables Usually Affected: var_vision_intensity, var_vision_doubt
- Narrative Meaning: Sustains ambiguity at increasing intensity rather than resolving it
- Gameplay Impact: Gates access to Chapter 2–3 level Emotion-purpose content
- Writer Notes: Each escalation must be paired with a concurrent mundane explanation, per Story_Map.md Mystery Escalation
- QA Notes: Verify var_vision_doubt never collapses to a fixed extreme before Chapter 4

### EVT-PSY-03: Impressions Intersect Personal History
- Event Name: Impressions Intersect Personal History
- Category: Psychological
- Description: An impression directly intersects with content revealed through the Family Secret Opened event.
- Triggered By: An Emotion-purpose scene immediately following EVT-FAM-02
- Required Active States: PSY-02, FAM-02
- Required Variables / Flags: None beyond prerequisite states
- State Changes: Enters PSY-03 (Impressions Intersect Personal History)
- Variables Usually Affected: var_vision_intensity, var_vision_doubt
- Narrative Meaning: The personal and historical mystery threads visibly converge in Daniel's experience
- Gameplay Impact: Required precondition for the climactic Chapter 4 impression
- Writer Notes: Must still permit a fully mundane reading (e.g., suggestibility following disclosure) alongside the inherited-memory reading
- QA Notes: Confirm this event cannot fire before EVT-FAM-02

### EVT-PSY-04: Final Impression
- Event Name: Final Impression
- Category: Psychological
- Description: Daniel's final, climactic impression occurs at the same moment as the caravan's historical resolution.
- Triggered By: Chapter 4's climactic Emotion-purpose scene, concurrent with EVT-INV-04
- Required Active States: PSY-03, INV-04
- Required Variables / Flags: None beyond prerequisite states
- State Changes: Enters PSY-04 (Ambiguity Sustained at Climax)
- Variables Usually Affected: var_vision_intensity, var_vision_doubt
- Narrative Meaning: The story's defining ambiguity is preserved at its highest emotional stakes
- Gameplay Impact: Hard gate on Final Disclosure and every ending
- Writer Notes: No scene, document, or character line associated with this event may tip the ambiguity decisively in either direction
- QA Notes: Highest-priority QA gate in the package; every ending must be checked against this event's narrative meaning

---

## Social Events

### EVT-SOC-01: Local Guide Trust Established
- Event Name: Local Guide Trust Established
- Category: Social
- Description: Daniel's presence at the excavation becomes socially established through the Local Guide.
- Triggered By: A Character-purpose scene in which Daniel and the Local Guide build initial working trust
- Required Active States: None (entry-tier event within this category)
- Required Variables / Flags: flag_met_local_guide true
- State Changes: Enters SOC-01 (Site Confirmed)
- Variables Usually Affected: var_map_knowledge, var_trust_local_guide
- Narrative Meaning: Daniel is no longer an unknown outsider at the site
- Gameplay Impact: Unlocks community-gated Discovery and Character content
- Writer Notes: This event establishes awareness, not trust depth — trust level is tracked separately via var_trust_local_guide
- QA Notes: Confirm flag_met_local_guide is true before any scene assumes community familiarity with Daniel

### EVT-SOC-02: Rival Becomes Active
- Event Name: Rival Becomes Active
- Category: Social
- Description: The Rival Treasure Hunter begins actively and visibly competing for access to the excavation's findings.
- Triggered By: A Conflict-purpose scene in Chapter 2 introducing direct competitive pressure
- Required Active States: SOC-01, INV-02
- Required Variables / Flags: None beyond prerequisite states
- State Changes: Enters SOC-02 (Rival Active)
- Variables Usually Affected: var_evidence_progress, var_reputation
- Narrative Meaning: External competitive pressure becomes a live narrative force
- Gameplay Impact: Introduces time-sensitive Decision content and potential Conflict escalation
- Writer Notes: The Rival's activity must escalate independently of player choice to some degree
- QA Notes: Confirm this event cannot fire before EVT-INV-02

### EVT-SOC-03: Social Outcome Settled
- Event Name: Social Outcome Settled
- Category: Social
- Description: Daniel's professional reputation and competitive standing reach their final state.
- Triggered By: The Final Disclosure event
- Required Active States: SOC-02
- Required Variables / Flags: None beyond prerequisite states
- State Changes: Enters SOC-03 (Social Outcome Settled)
- Variables Usually Affected: var_reputation
- Narrative Meaning: The social/professional thread's outcome becomes part of the locked ending
- Gameplay Impact: Feeds Ending Locked
- Writer Notes: Must support outcomes ranging from professional vindication to discredit
- QA Notes: Verify every ending maps to a specific, consistent SOC-03 value

---

## Black Market Event

### EVT-SOC-04: Black Market Offer Made
- Event Name: Black Market Offer Made
- Category: Social
- Description: The Crow makes a concrete black-market offer to Daniel for excavation findings.
- Triggered By: A Decision-purpose scene following EVT-INV-02, once The Crow has been introduced
- Required Active States: INV-02
- Required Variables / Flags: flag_met_crow true
- State Changes: No state transition by itself; raises var_black_market_exposure toward thresholds required by later Legal and Ending events
- Variables Usually Affected: var_black_market_exposure, var_money
- Narrative Meaning: Converts the latent black-market temptation established in Chapter 1 into an active, costed choice
- Gameplay Impact: Engaging this offer raises var_black_market_exposure, narrowing safer paths later without granting guaranteed benefit
- Writer Notes: Must present a genuine financial benefit alongside genuine escalating risk; never a one-sided trap or a one-sided windfall
- QA Notes: Confirm this event cannot fire before flag_met_crow is true and EVT-INV-02 has fired

---

## Convergence Events

### EVT-CONV-01: Final Disclosure
- Event Name: Final Disclosure
- Category: Convergence
- Description: Daniel makes his final, irreversible decision on what to disclose, to whom, and at what cost.
- Triggered By: Chapter 4's single decisive Decision scene
- Required Active States: INV-04, LEG-03, FIN-03, PSY-04; FAM-03 reachable concurrently
- Required Variables / Flags: None beyond the joint state preconditions
- State Changes: Enters CONV-01 (Final Disclosure); immediately triggers EVT-FIN-04, EVT-LEG-03, EVT-FAM-03 (if not already fired), EVT-SOC-03
- Variables Usually Affected: All Resource, Social, Legal, Relationship, and Psychological variables at their pre-ending values
- Narrative Meaning: The single decisive narrative moment determining which ending is reached
- Gameplay Impact: The last Decision-purpose content in the game
- Writer Notes: Must be written as one clearly identifiable decisive moment, not a diffuse series of small choices
- QA Notes: Verify all joint preconditions are independently satisfiable without forcing a single linear path to this event

---

## Ending Event

### EVT-END-01: Ending Locked
- Event Name: Ending Locked
- Category: Ending
- Description: The final ending category is determined and fixed; the playthrough is narratively complete.
- Triggered By: Immediate resolution following EVT-CONV-01
- Required Active States: CONV-01
- Required Variables / Flags: None beyond CONV-01's own preconditions
- State Changes: Enters CONV-02 (Ending Locked)
- Variables Usually Affected: All variables at their final values
- Narrative Meaning: The playthrough's complete story becomes fixed and legible as a coherent whole
- Gameplay Impact: Triggers ending-specific content per Story_Map.md Ending Structure
- Writer Notes: Confirm the resolved combination of LEG-04, FIN-04, FAM-03, SOC-03, and PSY-04 values matches one of the defined ending categories in Story_Map.md
- QA Notes: Final QA gate; no playthrough may reach this event without every terminal state in every category having a defined, consistent value
