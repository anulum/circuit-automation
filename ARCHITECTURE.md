<!--
SPDX-License-Identifier: AGPL-3.0-or-later
Commercial license available
© Concepts 1996–2026 Miroslav Šotek. All rights reserved.
© Code 2020–2026 Miroslav Šotek. All rights reserved.
ORCID: 0009-0009-3560-0851
Contact: www.anulum.li | protoscience@anulum.li
CIRCUIT-AUTOMATION — repository foundation
-->

# Architecture

## Current executable surface

The checkout contains:
- repository validation tooling;
- dedicated tests;
- workflow definitions;
- native documentation.

No domain component of Circuit Automation is implemented yet. The metadata keeps domain capabilities, claims and qualified record formats empty.

## Intended data flow

1. **Driver, capability and cell definition** bind qualified machine drivers, facility readiness and `ESD`/laser/battery interlock rules.
2. **Surface clamping** publishes the watched file, config, component, socket and JTAG/debug clamp list that refuses unapproved agent software effects across all five effect classes.
3. **Journalled execution and telemetry** record admitted commands on a calibrated timebase and stream native state observations.
4. **Fault reconciliation and lockout recovery** halt on envelope breach, verify sub-`50 V` bleed and `LOTO` isolation, and require person-in-role reconciliation.

## Ownership

**This project owns** the planned Circuit Automation records and boundary rules.

**Owned elsewhere:**

| Responsibility | Owner |
|---|---|
| admission and person-in-role approval verification | Circuit Core |
| board surface inventories and facility readiness | Circuit Technology |
| lot routes, recipes, genealogy and work orders | Circuit Manufacturing |
| bench measurement capture | Circuit Lab |
| recipe and cell qualification sign-off | Circuit Acceptance |

## Interpretation

- **Software clamps.** Passing a software or OS/firewall refusal probe does not certify physical emergency-stop hardware.

Read [the documentation architecture](docs/ARCHITECTURE.md) for the planned records, domain rules and schema identifiers.
