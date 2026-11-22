<!--
SPDX-License-Identifier: AGPL-3.0-or-later
Commercial license available
© Concepts 1996–2026 Miroslav Šotek. All rights reserved.
© Code 2020–2026 Miroslav Šotek. All rights reserved.
ORCID: 0009-0009-3560-0851
Contact: www.anulum.li | protoscience@anulum.li
CIRCUIT-AUTOMATION — repository foundation
-->

# Circuit Automation

Circuit Automation is being built on the planned manufacturing path to define equipment and workcell profiles, robotic handling tasks, command journals, state reconciliation, lockout-tagout recovery plans and the platform-wide equipment input-surface clamp registry — operating deterministically without AI and never substituting software checks for hardwired emergency stops. This checkout contains repository validation tooling and documentation only. Full foundation qualification is in progress. There is no installed equipment controller, robotics runner, surface-clamp daemon or qualified record schema.

**What does not exist yet:**
- an equipment driver, robotic cell controller or clamp-enforcement daemon;
- a registered runtime record schema;
- any connected factory cell, robot or physical machine.

## Boundary

**What this project owns:**

| Record | Scope |
|---|---|
| Equipment profile, cell profile and resource reservation | Machine capabilities, `SECS/GEM` or `OPC UA` protocol endpoints, process-capability bounds, multi-tool cell zoning and exclusive time-bounded reservations |
| Robot task, command event, state observation and reconciliation record | Bounded motion/gripper trajectories with electrostatic-dissipative (`ESD`) tooling checks, journalled command dispatches, native telemetry streams and post-fault state reconciliation |
| Autonomy envelope (safety interlock and clamp registry) | Hard safety envelopes, `IEC 60825-1` Class 3B/4 laser interlocks (zero unattended open-beam operation), lithium-ion thermal-runaway interlocks and the complete equipment/board input-surface clamp registry (watched paths, configuration targets, component IDs, network ports such as `SSH`, `Jupyter`, `TCP 3121` `hw_server` and `OpenOCD`, plus local `USB-JTAG` / `devcfg` / scan surfaces) |
| Recovery plan | Deterministic fault-recovery sequence enforcing sub-`50 V` stored-energy capacitor bleed verification and lockout-tagout (`LOTO`) state before human entry or restart |

**Static imports:** only Circuit Core and Circuit Technology.

**Records read without importing domain code:**

| Source | Records consumed |
|---|---|
| Circuit Core and Circuit Technology | entity references, operation requests, admissions, operation profiles, person approvals and prototyping board surface profiles |
| Circuit Acceptance | driver and recipe qualification records |
| Circuit Lab | timebase associations and calibration certificates |
| Circuit Manufacturing and Circuit Flow | qualified recipe releases, material states and design-step learning records |

**Capability registration and handoffs:** Registers the cell and robotics tool-profile manifests with Circuit Core and supplies native observations and input-surface clamp envelopes to Circuit Core, Circuit Flow, Circuit Lab, Circuit Prototyping, Circuit Manufacturing, Circuit Acceptance, Circuit Workbench and Neuro Evidence Bench.

**Explicit non-claims and operating boundaries:**
- It belongs to the planned manufacturing path and imports only Circuit Core and Circuit Technology — zero Circuit Manufacturing imports — keeping the architecture strictly acyclic.
- Software autonomy envelopes never replace hardwired local emergency stops, safety relays or physical interlocks.
- Its input-surface clamp registry blocks all five software-effect classes (`file`, `git_publication`, `deployment`, `migration`, `component_state`) from touching listed equipment, board, JTAG or debug surfaces without an enrolled person-in-role approval.

## Current tooling

Repository controls inspect:
- metadata and source attribution;
- workflows and dependency alignment;
- native documentation and repository inventory;
- preflight orchestration.

Metadata declares architecture-only maturity with empty implemented domain capability and claim inventories.

- Use the exact environment in [Contributing](CONTRIBUTING.md).
- Full CI and preflight belong in CI or in an explicitly admitted pre-push environment.
- See [Validation](VALIDATION.md) for the maintained validation scope.

## Intended evidence

Every future domain artefact will carry the platform's common provenance envelope, its source and environment digests, its confidentiality compartment and its explicit verification boundary. None of the planned record schemas is registered or qualified by this foundation.

## Documentation and support

Read [Architecture](ARCHITECTURE.md), [support](SUPPORT.md), [security reporting](SECURITY.md) and [citation metadata](CITATION.cff).

**Not claimed:**
- a hosted service, released package or DOI;
- a public CI status;
- a performed simulation, hardware measurement or sign-off verdict.

## Licence

Source is licensed under [AGPL-3.0-or-later](LICENSE). A commercial licence is available through the contact in [NOTICE](NOTICE.md).

![ANULUM](docs/assets/anulum_logo_company.jpg)

![Fortis Studio](docs/assets/fortis_studio_logo.jpg)

## Text and data mining reservation
The rightsholder, Miroslav Šotek (ANULUM), expressly reserves the use of the
works in this repository for text and data mining, including the collection of
this content for, and its use in, training, fine-tuning or evaluating machine
learning and artificial intelligence models, in accordance with Article 4(3) of
Directive (EU) 2019/790 and the national provisions transposing it.

No permission for such use has been granted beyond what the licence in
`LICENSE` grants. This reservation does not change that licence: uses the
licence permits remain permitted on its terms, including its attribution and
share-alike conditions.

Reservation made on 2026-11-22. Requests for permission: contact the
rightsholder through the contact listed in this repository.
