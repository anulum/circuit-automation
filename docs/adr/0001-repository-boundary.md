<!--
SPDX-License-Identifier: AGPL-3.0-or-later
Commercial license available
© Concepts 1996–2026 Miroslav Šotek. All rights reserved.
© Code 2020–2026 Miroslav Šotek. All rights reserved.
ORCID: 0009-0009-3560-0851
Contact: www.anulum.li | protoscience@anulum.li
CIRCUIT-AUTOMATION — repository foundation
-->

# Decision: isolate equipment drivers, robotics, lockout recovery and the input-surface clamp registry in Circuit Automation

## Context

An AI or workflow agent with file, deployment or network-socket permissions could accidentally trigger a board programmer, debug daemon or workcell controller unless every physical control surface is enumerated in one clamp registry imported cleanly without manufacturing cycles.

## Decision

**What Circuit Automation owns:**
- equipment profile, cell profile and resource reservation;
- robot task, command event, state observation and reconciliation record;
- autonomy envelope (safety interlock and clamp registry);
- recovery plan;

**What it imports:** only Circuit Core and Circuit Technology.

**Owned elsewhere:**

| Responsibility | Owner |
|---|---|
| admission and person-in-role approval verification | Circuit Core |
| board surface inventories and facility readiness | Circuit Technology |
| lot routes, recipes, genealogy and work orders | Circuit Manufacturing |
| bench measurement capture | Circuit Lab |
| recipe and cell qualification sign-off | Circuit Acceptance |

## Consequences

**What can be qualified now:** repository governance and validation tooling, before domain code exists.

**What it cannot qualify:** unimplemented schemas, solvers, hardware or sign-off verdicts.

**Architectural consequences:**
- Circuit Automation imports only Circuit Core and Circuit Technology, owning `autonomy_envelope` (`circuit_automation.autonomy_envelope.v1` first, for board-surface clamping) and the eight companion cell/equipment records;
- hardwired emergency stops and human-in-role approvals remain non-bypassable.
