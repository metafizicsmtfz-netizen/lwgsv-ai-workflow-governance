# LoosiesWorld Graduate School of Vehicle Abuse

**An AI-assisted driver development and workflow governance system built for Assetto Corsa.**

This project uses sim racing as the domain, but the real work is broader: structured data intake, state tracking, prompt governance, output validation, and human-in-the-loop AI coaching.

## What this is

LoosiesWorld Graduate School of Vehicle Abuse (LWGSVA) is a personal AI-assisted coaching system built around Assetto Corsa driving sessions. It takes session context, telemetry exports, driver self-reports, car/track data, and rule-based validation files, then uses AI to generate structured coaching feedback.

The project is not a machine learning model and does not train neural networks. It is a workflow system designed to make general-purpose AI behave more reliably inside a narrow, rule-heavy domain.

## The problem

General AI tools can be powerful, but they drift.

They can:
- invent outputs that were never requested,
- ignore established constraints,
- confuse session state,
- over-explain instead of coaching,
- produce invalid combinations,
- contradict prior rules,
- or sound confident while being wrong.

For this project, those problems mattered. The system needed to remember driver progression, respect session rules, validate car and track selections, keep environment output consistent, and produce useful coaching instead of generic feedback.

The goal became larger than "make AI coach sim racing." The goal became:

> Can domain knowledge, structured inputs, validation rules, and state management make AI output more reliable?

## What the system does

At a high level, LWGSVA:

1. Collects structured session information before the AI sees it.
2. Tracks driver progress over time using CSV-based state.
3. Uses catalogs and schemas to define valid cars, tracks, modes, environments, and session states.
4. Applies rules that prevent AI from freehanding invalid outputs.
5. Parses telemetry/session data and turns it into coaching feedback.
6. Incorporates driver self-report as first-class context.
7. Records progress so each session builds on the last one.

The system treats AI as a reasoning and writing layer, not as an unchecked authority. The surrounding files define the boundaries.

## Why I built it

The project started small: I noticed an exhaust flame effect in Assetto Corsa looked wrong, opened configuration files, realized they were editable text, and started changing things.

That became a larger pattern: inspect the system, understand the files, test a change, document the result, and build rules around what works.

Over time, that grew into a full AI-assisted driver development lab: a structured intake process, Python telemetry tools, session packaging, progress tracking, and a governance layer designed to catch and correct AI failure modes.

## Core architecture

```text
Human driver
   ↓
Session intake / self-report
   ↓
Structured files and state
   ↓
Python parsing and validation
   ↓
AI coaching layer
   ↓
Driver feedback, scoring, next objective
   ↓
Ledger update / session continuity
```

## Tech stack

- **Python** for parsing, validation, session assembly, telemetry support, and automation scripts
- **CSV files** for progress ledgers, car/track catalogs, and state management
- **JSON schemas** for strict output structure and validation
- **HTML** for a simplified intake-console pattern
- **Markdown** for project documentation, case studies, and public explanation
- **AI-assisted workflow design** for coaching narrative, analysis, and rule iteration

## What makes this portfolio-worthy

The strongest part of this project is not the sim racing theme. It is the governance layer.

I built rules because the AI made mistakes. Then I turned those mistakes into constraints. When outputs drifted, I added validation. When state was lost, I added ledgers. When generic advice was too vague, I tightened the output contract. When the AI freehanded invalid combinations, I pushed selection logic through controlled files.

That is the transferable skill:

> Knowing when AI is wrong, then building a system that makes the same failure harder to repeat.

## Key features

### Structured intake

The system asks for session mode, discipline, driver technical level, evaluation status, priority, self-report, car/track context, and telemetry package information before analysis begins. This reduces ambiguity and helps the AI produce more consistent output.

### State management

Driver progress is tracked across sessions instead of starting over every time. The project uses CSV and JSON files to preserve standing, session state, combo history, and validation context.

### Output validation

Environment blocks, session states, discipline profiles, and structured outputs are constrained by schema/rule files. If a required field is missing, out of order, or invalid, the system is designed to fail closed instead of producing a polished but wrong answer.

### AI failure-mode handling

The project explicitly accounts for AI behaviors such as:
- hallucinated fields,
- scope drift,
- invalid substitutions,
- forgotten prior state,
- incorrect scoring totals,
- excessive or irrelevant output,
- and unsupported assumptions.

### Human-in-the-loop design

Driver self-report is treated as real data. The system combines subjective context with objective telemetry instead of pretending numbers explain everything.

## Repository contents

```text
.
├── README.md
├── PROJECT_STRUCTURE.md
├── docs/
│   ├── CASE_STUDY_output_governance.md
│   └── GITHUB_UPLOAD_STEPS.md
└── examples/
    ├── sample_intake_console.html
    └── sample_validation_rules.json
```

This public repository is a sanitized portfolio version. It is intended to show the system design, workflow thinking, and AI governance approach without exposing the full private working project.

## Example governance idea

A simplified validation rule might say:

```json
{
  "rule_name": "closed_environment_block",
  "purpose": "Prevent AI from inventing extra environment fields.",
  "required_order": [
    "Season",
    "Hemisphere lock",
    "Local start time",
    "Weather script and controller",
    "PP filter",
    "Initial Grip (%)",
    "Ambient temp (°F)"
  ],
  "failure_behavior": "Abort output and regenerate through the validator."
}
```

The important idea is not the specific fields. The important idea is that AI output is treated like something that needs QA.

## What I learned

- AI works better when the input is structured before the prompt.
- Domain knowledge matters because it lets you catch confident wrong answers.
- Prompting alone is not enough; recurring failures need rules, schemas, and validation.
- CSV and JSON can be enough to build useful state management before a full database is needed.
- A personal project can become a real workflow system when the rules are documented.
- Human context and technical data can coexist in one feedback loop.

## Transferable applications

Although this was built around sim racing, the architecture could apply to:

- coaching workflows,
- technical support triage,
- QA checklists,
- onboarding systems,
- training programs,
- field reports,
- performance tracking,
- internal documentation systems,
- or any domain where AI needs strict guardrails.

## Project status

This is an independently built personal project and portfolio artifact. It is still evolving, but the core value is already visible: structured AI workflow design, practical automation, validation thinking, and careful documentation of failure modes.

## Positioning statement

I built this project to turn a complex personal learning system into something repeatable, testable, and explainable. It demonstrates how I use AI as a working partner while still applying human judgment, domain knowledge, and process discipline.
