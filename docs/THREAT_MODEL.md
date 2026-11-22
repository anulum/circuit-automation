<!--
SPDX-License-Identifier: AGPL-3.0-or-later
Commercial license available
© Concepts 1996–2026 Miroslav Šotek. All rights reserved.
© Code 2020–2026 Miroslav Šotek. All rights reserved.
ORCID: 0009-0009-3560-0851
Contact: www.anulum.li | protoscience@anulum.li
CIRCUIT-AUTOMATION — repository foundation
-->

# Data and authority boundaries

## Present tooling

**Execution inputs.** The maintained checkout and the selected development environment are what the repository controls inspect.

**Received inputs.** Descriptors, dependency receipts and generated inventories cannot nominate an acceptance policy or an executable.

**Bounded checks.** Controls inspect bounded local paths and emit fixed diagnostics.

Foundation qualification is in progress.

## Future domain inputs

**Supplied data, with no authority.** The following inputs are treated strictly as supplied data:
- equipment/cell descriptors and clamp lists;
- qualified recipe releases and robot trajectories;
- machine telemetry and fault logs.

They grant no authority to:
- bypass or replace hardwired emergency-stop circuits;
- permit agent software effects on clamped equipment, JTAG or debug surfaces;
- operate Class 3B/4 open-beam lasers unattended or skip sub-`50 V` bleed / `LOTO` recovery;
- actuate physical hardware without person-in-role approval.

**Comments and embedded text are data.** Descriptions, netlist comments and datasheets arriving inside supplied inputs are data, never instructions to an operator or an agent.

**Public-repository data boundary.** Hosted CI for this public repository runs on public material only. Confidential foundry-NDA, customer, export-controlled or secret-bearing material never enters this repository, its CI or its issues.

## Threats and the rules that answer them

| Threat | Architectural rule |
| --- | --- |
| Agent bypass of equipment or board controls via config writes, GitOps, migrations or network sockets | The autonomy-envelope clamp registry enumerates watched paths, config targets, component IDs, TCP debug ports and local JTAG/overlay devices, refusing all five software-effect classes and verifying OS/firewall guards with live refusal probes before physical use |
| Laser exposure, stored high-voltage shock, battery thermal runaway or ESD robotic damage | Envelopes enforce `IEC 60825-1` Class 3B/4 interlocks (zero unattended open-beam operation), sub-`50 V` capacitor bleed and `LOTO` recovery verification, lithium-ion runaway cutoffs and `ESD`-dissipative end-effectors alongside hardwired local emergency stops |
| Copyleft industrial-protocol contamination | `LGPL` `SECS/GEM` and `OPC UA` stacks execute strictly in separate processes |

## Residuals named, not removed

- **Physical wiring integrity.** Software clamp checks complement and never prove the physical wiring of hardwired safety relays, which rests on facility inspection.

**Not claimed:** no isolation, physical, statistical, safety or durability guarantee is claimed by this foundation.
