---
icon: lucide/pencil-ruler
---

# Editing the documentation

This page explains how to maintain the ROX-Diff documentation using the Zensical documentation style.

## Initial setup

To edit the documentation, clone the repository and setup the virtual environment (venv)

``` bash title="Environment setup"
git clone https://github.com/Huxyshuu/NeobotixAalto
python3 -m venv venv
source venv/bin/activate
pip install zensical
```
## Previewing local changes

To preview the live changes from local files, ensure that you have activated the venv and are in the right folder, then run:

``` bash title="Preview the site"
# Make sure you have activated the venv from previous step
cd NeobotixAalto
zensical serve
```

Building the static site is not necessarily needed, since any merged pull requests will be automatically updated to the documentation. Nevertheless, the static site can be built with:

``` bash title="Build the site"
zensical build
```

!!! note

    Keep page names concise and stable. Don't change them later in the future, since other parts of the documentation may refer to them and the links might break.

## Current page structure

All changes done to the documentation should focus on the *docs* directory
``` text title="Overview of docs directory"
docs/
├── index.md
├── setup.md
├── documentation.md
...
...
├── safety.md
└── Projects 
  ├─ index.md
  ...
  ...
  ├── instructions.md
  └── Template
```

## Adding documentation for new projects

Adding or editing documentation for projects done on the ROX, please refer to the [instructions](Projects/instructions.md) in the *Projects/* folder. 

## Writing style

When editing documentation for the robot, or creating new projects or other pages, please follow the general style convention used for rest of the pages. This keeps the overall documentation clean and readable for everyone. Aim to write clear instructions:

- write commands that can be copied and tested
- explain where local values must be filled in;
- separate public information from private Aalto/lab information;
- prefer checklists for operation and safety steps;
- include necessary warnings for steps that can move the robot or affect safety;
- link to official Neobotix/ROS documentation instead of copying long sections.

## Useful Zensical patterns

### Admonitions

``` markdown title="Admonition example"
!!! warning "Verify before motion"

    Confirm the safety state before sending velocity commands.
```
!!! warning "Verify before motion"

    Confirm the safety state before sending velocity commands.

### Collapsible details

``` markdown title="Details example"
??? info "Troubleshooting"

    Add longer diagnostic notes here.
```
??? info "Troubleshooting"

    Add longer diagnostic notes here.


### Content tabs

``` markdown title="Tabs example"
=== "Real robot"

    Instructions for the physical robot.

=== "Simulation"

    Instructions for Gazebo or offline testing.
```
=== "Real robot"

    Instructions for the physical robot.

=== "Simulation"

    Instructions for Gazebo or offline testing.

### Mermaid diagrams

```` markdown title="Mermaid example"
``` mermaid
graph LR
  A[Client PC] --> B[Robot PC]
  B --> C[ROS 2 topics]
```
````
``` mermaid
graph LR
  A[Client PC] --> B[Robot PC]
  B --> C[ROS 2 topics]
```

## Documentation checklist for maintainer, don't worry about this

- [ ] Add local robot identity and maintainer information.
- [ ] Add exact robot network procedure in a protected/internal page.
- [ ] Add verified launch commands for the delivered robot.
- [ ] Add the current map and navigation workflow.
- [ ] Add approved charging procedure.
- [ ] Add experiment log storage location.
- [ ] Review safety page with the responsible lab person.
