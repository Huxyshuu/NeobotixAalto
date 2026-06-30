---
icon: lucide/pencil-ruler
---

# Editing the documentation

This page explains how to maintain the ROX-Diff documentation using the Zensical documentation style.

## Local preview

From the documentation project root, run:

``` bash title="Preview the site"
zensical serve
```

Build the static site with:

``` bash title="Build the site"
zensical build
```

!!! note

    Keep page names short and stable. Other project notes, lab procedures, and experiment reports may link to them.

## Current page structure

``` text title="Recommended docs directory"
docs/
├── index.md
├── setup.md
├── operation.md
├── research.md
├── safety.md
└── documentation.md
```

## Writing style

Use a practical, lab-oriented style:

- write commands that can be copied and tested;
- explain where local values must be filled in;
- separate public information from private Aalto/lab information;
- prefer checklists for operation and safety steps;
- include warnings for steps that can move the robot or affect safety;
- link to official Neobotix documentation instead of copying long sections.

## Useful Zensical patterns

### Admonitions

``` markdown title="Admonition example"
!!! warning "Verify before motion"

    Confirm the safety state before sending velocity commands.
```

### Collapsible details

``` markdown title="Details example"
??? info "Troubleshooting"

    Add longer diagnostic notes here.
```

### Content tabs

``` markdown title="Tabs example"
=== "Real robot"

    Instructions for the physical robot.

=== "Simulation"

    Instructions for Gazebo or offline testing.
```

### Mermaid diagrams

```` markdown title="Mermaid example"
``` mermaid
graph LR
  A[Client PC] --> B[Robot PC]
  B --> C[ROS 2 topics]
```
````

## Documentation checklist

- [ ] Add local robot identity and maintainer information.
- [ ] Add exact robot network procedure in a protected/internal page.
- [ ] Add verified launch commands for the delivered robot.
- [ ] Add the current map and navigation workflow.
- [ ] Add approved charging procedure.
- [ ] Add experiment log storage location.
- [ ] Review safety page with the responsible lab person.
