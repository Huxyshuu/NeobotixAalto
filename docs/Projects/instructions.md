---
icon: lucide/list-checks
---

# Instructions for documenting projects

Use this page when creating a new project entry under `docs/Projects/`. The project can be a research activity, thesis/student project, integration test, temporary benchmark, hardware trial, or internal demo.

!!! success "Main rule"

    Document the project so that a new person can understand the goal, rebuild the setup, run the main workflow, find the outputs, and know what is safe or unsafe without asking the original maintainer.

## When to create a new project folder

Create a new folder when the work has any of the following:

| Case | Create project folder? | Example |
|---|---:|---|
| Research experiment | Yes | Navigation benchmark, fleet coordination, digital twin integration |
| Student project | Yes | Master's thesis experiment, course project, summer assistant work |
| Temporary test | Yes, if it changes setup or creates reusable results | Testing a new sensor driver or ROS 2 package |
| One-off note | Usually no | Meeting note with no technical output |
| Platform-wide procedure | No, put it in main docs | General robot startup, charging, safety procedure |

## Naming convention

Use a stable lowercase slug:

``` text
YYYY-short-topic-name
```

Good examples:

``` text
2026-navigation-benchmark
2026-fleet-digital-twin-demo
2026-lidar-mount-test
2026-student-thesis-person-following
```

Avoid names such as:

``` text
new-test
saad-project
final-version
robot-stuff
```

!!! warning "Avoid personal-only names"

    Names should describe the project topic, not only the person. People leave; project topics remain searchable.

## Recommended project folder layout

=== "Small project"

    Use this for short tests or early prototypes.

    ``` text
    docs/Projects/2026-example-test/
    ├── index.md
    └── assets/
    ```

=== "Normal project"

    Use this for research, student, and integration projects.

    ``` text
    docs/Projects/2026-example-project/
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

=== "Large project"

    Use this when the project has several work packages or multiple maintainers.

    ``` text
    docs/Projects/2026-example-large-project/
    ├── index.md
    ├── setup.md
    ├── operation.md
    ├── architecture.md
    ├── experiments/
    │   ├── index.md
    │   ├── experiment-001.md
    │   └── experiment-002.md
    ├── troubleshooting.md
    ├── handover.md
    └── assets/
    ```

## How to create a new project page

1. Create a new folder under `docs/Projects/`.
2. Copy [the project template](template.md) into the new folder as `index.md`.
3. Replace every `TODO` placeholder.
4. Add setup commands that have been tested from a clean workstation.
5. Add links to repositories, data folders, configuration files, and maps.
6. Add screenshots, diagrams, or photos under the project `assets/` folder.
7. Add the project to `zensical.toml` navigation if explicit navigation is used.
8. Run a local documentation preview and check that links work.

``` bash title="Preview documentation"
zensical serve
```

``` bash title="Build documentation"
zensical build
```

## What good documentation should answer

A future maintainer should be able to answer these questions from the project page:

- What was the project trying to achieve?
- Who worked on it and when?
- What exact robot, PC, ROS 2 distribution, branch, map, and configuration were used?
- What commands start the system?
- What should the user see when the setup is working?
- Where are the logs, datasets, videos, maps, and results?
- What failed, what was not completed, and what should be done next?
- What must not be changed without checking with the robot maintainer?

## Required metadata block

Every project `index.md` should include this table near the top:

| Field | Value |
|---|---|
| Project type | TODO: Research / Student / Temporary test / Integration / Demo |
| Status | TODO: Planned / Active / Paused / Completed / Archived |
| Start date | TODO: YYYY-MM-DD |
| End date | TODO: YYYY-MM-DD or ongoing |
| Main maintainer | TODO: Name and contact |
| Backup contact | TODO: Name and contact |
| Related repository | TODO: Link or internal path |
| Data location | TODO: Link or internal path |
| Robot affected | TODO: ROX-Diff ID / none / simulation only |
| Safety impact | TODO: None / low / medium / high |

## Documentation quality checklist

Before archiving the project, check:

- [ ] All TODOs are removed or intentionally marked as unknown.
- [ ] Commands have been tested by someone other than the main maintainer.
- [ ] Required credentials are not written in public documentation.
- [ ] Old branches, temporary folders, and obsolete maps are marked clearly.
- [ ] Data and logs are linked, not silently stored on a personal laptop.
- [ ] Known failures and limitations are documented honestly.
- [ ] The project status is updated to completed, paused, or archived.
- [ ] The handover section explains what the next person should do.

!!! danger "Do not document secrets"

    Do not place passwords, private keys, VPN details, private Wi-Fi credentials, internal IPs, or access tokens in public documentation. Use protected internal storage and link to it only when appropriate.

