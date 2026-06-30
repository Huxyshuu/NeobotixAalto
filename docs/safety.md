---
icon: lucide/shield-alert
---

# Safety and lab rules

This page is a placeholder for local safety rules. It must be reviewed and completed by the responsible Aalto laboratory staff or robot maintainer.

!!! danger "Not a substitute for official safety documentation"

    Always follow Aalto laboratory rules, Neobotix manuals, project risk assessments, and supervisor instructions. This page is only a documentation scaffold.

## Minimum safety principles

- Operate the robot only in approved areas.
- Keep emergency stop access clear.
- Do not bypass safety scanners, emergency stops, or protective devices.
- Do not stand in the robot path during tests.
- Use low speeds for first tests after software, map, payload, or sensor changes.
- Stop immediately if motion, localization, braking, or obstacle detection behaves unexpectedly.
- Do not run autonomous tests when people are entering the test area without an agreed procedure.

## Stop conditions

Stop the experiment immediately if:

- the robot moves in an unintended direction;
- localization is lost;
- the safety scanner reports an unsafe state;
- a person enters the protected test area;
- a payload or trolley becomes unstable;
- communication with the robot becomes unreliable;
- battery, drive, or diagnostic warnings appear.

## Pre-test checklist

- [ ] Test area approved.
- [ ] Emergency stop checked.
- [ ] Safety scanner unobstructed.
- [ ] Robot speed limits appropriate for test.
- [ ] Operator and observer roles clear.
- [ ] Manual stop method confirmed.
- [ ] Log recording started, if required.

## Post-test checklist

- [ ] Robot stopped safely.
- [ ] Logs saved.
- [ ] Issues documented.
- [ ] Map/config changes committed or reverted.
- [ ] Robot returned to charging/storage state.
