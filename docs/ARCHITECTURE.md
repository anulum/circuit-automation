<!--
SPDX-License-Identifier: AGPL-3.0-or-later
Commercial license available
© Concepts 1996–2026 Miroslav Šotek. All rights reserved.
© Code 2020–2026 Miroslav Šotek. All rights reserved.
ORCID: 0009-0009-3560-0851
Contact: www.anulum.li | protoscience@anulum.li
CIRCUIT-AUTOMATION — repository foundation
-->

# Repository architecture

## Current executable tooling

**What it contains:** the repository's metadata, source-provenance, workflow, dependency-alignment, documentation, inventory and preflight controls.

**What each control does:** it inspects its fixed, declared local scope.

**What received metadata cannot do:** select another acceptance policy or grant domain authority.

Foundation qualification is in progress.

## Intended domain boundaries

| Record | Responsibility | Required evidence |
| --- | --- | --- |
| Equipment profile, cell profile and resource reservation | Machine capabilities, `SECS/GEM` or `OPC UA` protocol endpoints, process-capability bounds, multi-tool cell zoning and exclusive time-bounded reservations | Qualified driver digest, calibrated sensor links and facility-readiness prerequisites |
| Robot task, command event, state observation and reconciliation record | Bounded motion/gripper trajectories with electrostatic-dissipative (`ESD`) tooling checks, journalled command dispatches, native telemetry streams and post-fault state reconciliation | Synchronised laboratory timebase, zero unjournalled actuation and explicit person-approved reconciliation after aborts |
| Autonomy envelope (safety interlock and clamp registry) | Hard safety envelopes, `IEC 60825-1` Class 3B/4 laser interlocks (zero unattended open-beam operation), lithium-ion thermal-runaway interlocks and the complete equipment/board input-surface clamp registry (watched paths, configuration targets, component IDs, network ports such as `SSH`, `Jupyter`, `TCP 3121` `hw_server` and `OpenOCD`, plus local `USB-JTAG` / `devcfg` / scan surfaces) | Operating-system and firewall guards plus live real-surface agent-refusal probes before any physical machine or board is enabled |
| Recovery plan | Deterministic fault-recovery sequence enforcing sub-`50 V` stored-energy capacitor bleed verification and lockout-tagout (`LOTO`) state before human entry or restart | Person-in-role sign-off before clearing a faulted cell |

## Protocol and licence isolation

- **Separate-process industrial stacks.** `secsgem` (`LGPL-3.0`), `asyncua` (`LGPL-3.0`), `open62541` (`MPL-2.0`) and proprietary vendor equipment daemons run strictly in separate processes over bounded IPC/file channels; permissive robotics planners run under pinned container digests.

## Planned record schemas

- `circuit_automation.equipment_profile.v1`
- `circuit_automation.cell_profile.v1`
- `circuit_automation.robot_task.v1`
- `circuit_automation.command_event.v1`
- `circuit_automation.state_observation.v1`
- `circuit_automation.reconciliation_record.v1`
- `circuit_automation.autonomy_envelope.v1`
- `circuit_automation.recovery_plan.v1`
- `circuit_automation.resource_reservation.v1`

These are planned identifiers. None of them is registered or qualified here.

Read [validation tooling](validation-tooling.md) for the executable repository interfaces.
