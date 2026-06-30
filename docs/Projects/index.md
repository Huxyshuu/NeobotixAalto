---
icon: lucide/folder-kanban
---

# Project archive

This section collects research, student, integration, and temporary test projects that use or affect the ROX-Diff platform.

Each project should have its own folder under `Projects/` so that future users can understand what was done, reproduce the setup, find the data and code, and safely continue or retire the work after the original maintainer is no longer available.

!!! note "Purpose"

    The goal is not to create heavy bureaucracy. The goal is to make every project understandable after six months, one year, or after team members have changed.

## Recommended folder structure

Use one folder per project. Keep names short, stable, and lowercase.

``` text title="Recommended structure"
docs/
└── Projects/
    ├── index.md
    ├── instructions.md
    ├── template.md
    └── rox-navigation-benchmark-2026/
        ├── index.md
        ├── setup.md
        ├── operation.md
        ├── experiments.md
        ├── troubleshooting.md
        └── assets/
            ├── diagrams/
            ├── photos/
            └── configuration-snapshots/
```

For small temporary tests, a single `index.md` inside the project folder is enough. For larger research or student projects, split the content into setup, operation, experiments, and troubleshooting pages.

## Minimum documentation requirement

Every project folder should include at least:

- [ ] project summary and purpose
- [ ] responsible people and handover contact
- [ ] dates, status, and project type
- [ ] hardware and software used
- [ ] setup steps from a clean workstation
- [ ] run commands and expected outputs
- [ ] data, logs, maps, and configuration locations
- [ ] known issues and limitations
- [ ] safety notes and operating constraints
- [ ] archive checklist

## Templates

Start from the copyable page template:

- [Project page template](template.md)
- [Instructions for adding projects](instructions.md)

