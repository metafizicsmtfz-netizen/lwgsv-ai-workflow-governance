# Case Study: Turning AI Drift Into Output Governance

## Situation

The project began as an AI-assisted driver coaching system for Assetto Corsa. Early versions were useful, but the AI would sometimes produce confident outputs that violated the system's rules.

The issue was not that the AI was useless. The issue was that it needed boundaries.

A general-purpose AI could explain driving concepts, but a working coaching system needed continuity, valid session state, consistent fields, and domain-specific constraints.

## Failure mode

One recurring problem was output drift.

The AI might:
- add extra fields to structured blocks,
- rename required fields,
- use unsupported units,
- skip a required session state,
- generate a car/track/environment combination outside the controlled catalog,
- or produce generic analysis instead of the requested coaching format.

These failures looked polished, which made them dangerous. A wrong answer with confident formatting can be harder to catch than an obvious error.

## Response

I began treating AI output like something that needed QA.

Instead of only rewriting prompts, I created rules and validation files that defined what "valid" meant. The system moved from "ask AI for an answer" toward "prepare structured inputs, constrain the output, validate the result, then use AI for interpretation."

## Governance rules added

Examples of controls added to the workflow:

- **Closed schema outputs:** structured blocks can only use approved fields in approved order.
- **Fail-closed behavior:** if required catalogs or validators cannot be loaded, the system should not freehand an answer.
- **State-first generation:** current progress and session state must be read before new scored assignments.
- **Controlled selection universe:** cars, tracks, layouts, and environment pieces must come from verified files.
- **Telemetry trust exceptions:** unreliable channels are marked before they can affect scoring.
- **Output minimalism:** coaching output should focus on driver actions, not raw ingestion details.

## Result

The project became more reliable because every repeated AI failure became a design input.

The system did not depend on trust alone. It used:
- structured intake,
- CSV/JSON state,
- validation rules,
- catalog-controlled selections,
- and documented failure handling.

## What this demonstrates

This case study shows the most transferable part of the project:

> I can identify AI failure modes, translate them into requirements, and build practical guardrails around them.

The domain was sim racing, but the pattern applies to many workplace systems:
- support workflows,
- QA processes,
- training tools,
- onboarding systems,
- internal knowledge bases,
- field reporting,
- and any AI-assisted process where wrong-but-confident output creates risk.
