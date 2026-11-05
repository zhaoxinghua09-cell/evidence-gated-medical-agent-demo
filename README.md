# Evidence-gated lifecycle demo for a hospital-deployed medical AI agent

A dependency-free reference demo of a **runtime gate**: at the moment an agent
acts, the gate decides whether *this* registered agent instance, on *this*
model version, may produce a finding — and re-decides when the model, its
evidence base, or the operating population changes. It consists of one Python
script and one JSON failure-rule catalog, using the standard library only.

This package exists to make a standardization use case concrete and
independently reproducible. It is **not** a product, a clinical validation, a
conformity assessment, or a claim of operational deployment.

## Quickstart

Run from the repository root, with `failure_rules.json` beside the script:

```bash
python lgd_medai_demo.py        # Python 3.10+, standard library only
```

Expected result: exit code `0`, `final_state = RESUMED`, and a lifecycle log
containing `DENIED`, `PAUSE`, `ROLLBACK` and `RESUMED` receipts.

Copying only `lgd_medai_demo.py` without `failure_rules.json` raises
`FileNotFoundError` at startup — the rule catalog is a required input, not an
optional extra. Download or clone the whole repository.

## What it models

| Act | Chain | Point illustrated |
|---|---|---|
| 1 | Register agent, model, tool and dataset | A registry of control-plane state that gates evaluate against |
| 2 | Evidence absent → `DENIED` → evidence supplied → gate admits | "Evidence absent" and "evidence found wrong" are distinct failure states |
| 3 | Model change → change gate → re-assessment → re-approval | Re-evaluation of previously accepted verdicts on upstream change |
| 4 | Monitoring → population drift (headline accuracy unchanged) → `PAUSE` → `ROLLBACK` → `REVERIFY` → `RESUMED` | Silent failure and the second half of the lifecycle, including non-monotonic eligibility |

Acceptance is **non-monotonic**: an accepted verdict can be suspended and later
restored. The demo prints a deterministic JSON audit receipt with a chain
digest so any third party can reproduce the run.

## Files

| File | Role |
|---|---|
| `lgd_medai_demo.py` | State machine, gate, monitoring and change gate (standard library only) |
| `failure_rules.json` | Required input: three example mappings from silent-failure signals to gate actions |
| `VERIFICATION.md` | How to verify this package independently |
| `ATTESTATION.md` | Authorship, licence boundaries, timestamps and integrity anchors |
| `manifest.json` | Machine-readable SHA-256 inventory of every file in this package |
| `LICENSE` | Apache-2.0 full text |

## Independent verification

Verification is the point of this package — please verify rather than trust.
See [VERIFICATION.md](VERIFICATION.md) for the acceptance contract and how to
report a passing or failing result. No credentials, accounts or network
services are required to run it.

## Licence and attestation

The **code** in this repository is licensed under **Apache-2.0** (see
[LICENSE](LICENSE)). Authorship, the machine-readable file inventory, the
timestamp and the integrity anchors are recorded in
[ATTESTATION.md](ATTESTATION.md) and [manifest.json](manifest.json).

This repository does not contain or license any theoretical corpus. No
statement is made here about the licence status of any external work.

## Scope and boundaries

- The scenario is **fictional**; no real patient data, clinical finding or
  hospital system is involved.
- This is a decision-support scenario with no physical actuation.
- It is **not** a medical device, **not** SaMD, **not** clinical advice, and
  must not be used for any clinical purpose.
- It does **not** claim alignment, certification or endorsement by any
  regulator, standards body or notified body. References to regulatory
  concepts elsewhere in the associated use case are conceptual mappings only.
- Registry, evidence and gate mechanisms each have prior art. This demo
  illustrates their **combination and a shared verdict vocabulary**; it does
  not claim novelty for any individual mechanism.
- A `DENIED` receipt is a transient state in this simplified demo (the state
  is re-registered directly). The normative semantics are defined in the
  associated use case's gate-decision record.
