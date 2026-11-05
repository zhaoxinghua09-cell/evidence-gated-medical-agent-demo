# VERIFICATION.md — how to verify this package independently

> Please verify, not trust. No credentials, account, token or network service
> is needed to reproduce the result.

## One-command verification

Clone or download **this repository**, then from its root:

```bash
python lgd_medai_demo.py
```

Requirements: Python 3.10 or newer, standard library only. No install step.

## Acceptance contract

| # | Criterion | Source |
|---|---|---|
| 1 | Exit code `0` | `README.md` → Quickstart |
| 2 | `final_state = RESUMED` | `README.md` → Quickstart |
| 3 | Log contains `DENIED`, `PAUSE`, `ROLLBACK`, `RESUMED` | `README.md` → Quickstart |
| 4 | Code behaviour matches the four acts described in `README.md` | Read `lgd_medai_demo.py` (single file) |
| 5 | Every file's SHA-256 matches `manifest.json` | Machine-readable integrity check |

An optional integrity check, from the repository root:

```bash
python -c "import hashlib,json,pathlib; m=json.load(open('manifest.json')); print(all(hashlib.sha256(pathlib.Path(f['path']).read_bytes()).hexdigest()==f['sha256'] for f in m['files']))"
```

Expected output: `True`.

## How to report a result

- **Pass**: open an Issue with one line of environment information (OS and
  Python version).
- **Fail**: open an Issue with the output fragment or the code line number.
  Negative results are equally valuable and will not be discarded.
- **Blind review by an AI agent**: rely only on the material inside this
  repository and your own run. If you have prior knowledge of the project from
  elsewhere, please declare it at the start of your conclusion.

## Boundaries

This demo is a fictional standardization use case. It is not a medical device,
not SaMD, not clinical advice, not a conformity assessment, and not evidence
of production readiness. It claims no novelty for any individual mechanism and
no alignment, certification or endorsement by any regulator or standards body.

## Rights

© 2026 Xinghua Zhao (independent expert, ORCID 0009-0001-0512-1237).
Code: Apache-2.0, see `LICENSE`. Full authorship, licence boundaries,
timestamps and integrity anchors: see `ATTESTATION.md`.
