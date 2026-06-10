# Project Structure Overview

This repository is organized as a public-facing portfolio version of the larger private project.

```text
.
├── README.md
│   Main public explanation of the project, problem, architecture, and learnings.
│
├── PROJECT_STRUCTURE.md
│   This file. A simple map of the repository.
│
├── docs/
│   ├── CASE_STUDY_output_governance.md
│   │   Short case study explaining how one AI failure mode became a validation rule.
│   │
│   └── GITHUB_UPLOAD_STEPS.md
│       Browser-only steps for creating and uploading the repository to GitHub.
│
└── examples/
    ├── sample_intake_console.html
    │   Simplified intake form showing how session context is structured before AI analysis.
    │
    └── sample_validation_rules.json
        Sanitized sample of the governance rules used to prevent invalid AI outputs.
```

## Full private system categories

The broader working project includes these categories:

```text
/private-working-system/
├── atlases/
│   ├── carAtlas_full.csv
│   └── trackAtlas_full.csv
│
├── state/
│   ├── driver_progress_ledger.csv
│   ├── session_state.json
│   └── options_state.json
│
├── validation/
│   ├── environment_schema.json
│   ├── validator.py
│   └── assembler.py
│
├── environment/
│   ├── weather_catalog.csv
│   ├── ppfilter_catalog.csv
│   └── compatibility_rules.csv
│
├── intake/
│   └── session_console.html
│
├── telemetry/
│   ├── recorder.py
│   ├── parsers/
│   └── session_packages/
│
└── docs/
    ├── system_manual.md
    ├── self_report_template.md
    └── case_studies/
```

The public repo intentionally shows the design pattern without publishing every private file, personal driver note, or full working catalog.
