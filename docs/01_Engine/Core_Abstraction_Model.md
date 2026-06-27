StoryVerse — Core Abstraction Model

Status: DRAFT
Version: 0.1
Owner: Executive Producer / System Architect

⸻

Purpose

This document defines the boundary between the StoryVerse Engine and Story Packages.

The engine must remain completely independent from any specific story, genre, culture, historical period or world.

⸻

Core Principle

The Engine understands abstractions.

Stories provide meaning.

The UI presents that meaning to the player.

⸻

Three-Layer Architecture

Layer 1 — Engine

The engine only understands abstract concepts.

It never understands story concepts.

Examples:

* Resource
* Vitality
* Social Metric
* Knowledge Metric
* Progress Metric
* Time
* Inventory
* Relationship
* State Flag
* Choice
* Condition
* Consequence

⸻

Layer 2 — Story Package

Each story maps abstract concepts into its own world.

Example:

Persian Treasure

Resource → Money

Vitality → Health

Knowledge Metric → Historical Knowledge

Progress Metric → Evidence

Social Metric → Trust

⸻

Mars Colony

Resource → Oxygen

Vitality → Suit Integrity

Knowledge Metric → Scientific Research

Progress Metric → Mission Progress

Social Metric → Crew Morale

⸻

Prison Escape

Resource → Influence

Vitality → Physical Condition

Knowledge Metric → Escape Knowledge

Progress Metric → Escape Plan

Social Metric → Gang Respect

⸻

Layer 3 — Presentation

The UI never displays abstract names.

It displays story-specific labels.

Example

Engine

Resource

↓

Story Mapping

Money

↓

UI

💰 Money: 150

⸻

Engine Responsibilities

The engine is responsible for:

* Scene flow
* Variable storage
* Choice evaluation
* Condition checking
* Consequence execution
* Save / Load
* Story loading

The engine is NOT responsible for:

* Story
* Characters
* History
* Lore
* Dialogue
* Worldbuilding

⸻

Story Responsibilities

A Story Package defines:

* Characters
* Locations
* Timeline
* Images
* Music
* Narrative
* Dialogue
* Variable Labels
* Assets

⸻

Asset Model

Assets are optional.

A Scene may contain:

* Image
* Music
* Ambient
* Sound Effects

Only Narrative Text is mandatory.

⸻

Choice Model

The engine understands only operations.

Examples:

* Gain Resource
* Lose Resource
* Gain Knowledge
* Lose Vitality
* Advance Time
* Unlock Flag
* Lock Flag
* Go To Scene

The engine never understands:

* Buy Train Ticket
* Pay Doctor
* Hire Archaeologist

Those belong to Story Packages.

⸻

Variable Categories

The engine defines only categories.

Stories define meanings.

Core categories:

* Resource
* Vitality
* Knowledge
* Progress
* Social
* Time
* Inventory
* Relationship
* State Flag

No additional category may be added to the engine without architectural review.

⸻

Golden Rule

Every new story must adapt itself to the engine.

The engine must never be modified to support a single story.