# ATTESTATION.md — authorship, integrity and boundaries

## 1. Package

| Field | Value |
|---|---|
| Package | Evidence-gated lifecycle demo for a hospital-deployed medical AI agent |
| Version | v0.1 (de-branded reference edition for standards use) |
| Author | Xinghua Zhao — independent expert, ORCID 0009-0001-0512-1237 |
| Contact | zhaoxinghua06@126.com |
| Generated at (UTC) | see `manifest.json` → `generated_at_utc` (machine-generated, not hand-written) |
| File inventory | see `manifest.json` → `files[]` (SHA-256 + byte size for every file, excluding `manifest.json` itself) |

© 2026 Xinghua Zhao. The code in this repository is licensed under
**Apache-2.0** (`LICENSE`). This attestation and the other documentation files
state facts and boundaries; they do not relicense the code.

## 2. Internal anchor

- Authorship and ORCID are written **inside** the files (`README.md`,
  `VERIFICATION.md`, `ATTESTATION.md`, `llms.txt`, `lgd_medai_demo.py`,
  `failure_rules.json`).
- Package name and version are stated in this section and in `manifest.json`.
- The canonical public repository URL is the URL of the repository hosting
  this package; it is deliberately not hard-coded inside the package so that
  the content stays self-consistent regardless of repository naming.

## 3. External anchor

The **public commit history of this repository on GitHub** is the external
anchor: every file is published through a separate commit, and each commit SHA
is recorded in the publication receipt. Any third party can verify the commit
history, the file contents and the commit timestamps without credentials.

`manifest.json` is self-excluded from its own hash list (a file cannot contain
its own digest). This is stated explicitly so that the omission is not read as
an integrity gap.

## 4. Integrity

`manifest.json` carries a SHA-256 digest and byte size for each file. The
one-line check in `VERIFICATION.md` recomputes all digests locally. Publication
verification additionally re-downloads a fresh archive of the public
repository and re-runs the demo from that clean copy — the result, not the
claim, is the evidence.

## 5. Licence boundaries

- The **code** (`lgd_medai_demo.py`, `failure_rules.json`) is Apache-2.0.
- This repository **does not contain any theoretical corpus** and makes **no
  statement** about the licence status of any external or theoretical work.
- Third-party project names appearing in this repository are used only as
  technical references; no affiliation, sponsorship or endorsement is implied.

## 6. Disclaimer and boundaries

Provided "AS IS", without warranty of any kind. The scenario is fictional and
contains no real patient data. This package is **not** a medical device,
**not** SaMD, **not** clinical advice, **not** a conformity assessment,
**not** a certification or endorsement by any regulator or standards body, and
**not** evidence of production readiness or deployment in any hospital.

Registry, evidence and gate mechanisms each have prior art; this demo
illustrates their combination and a shared verdict vocabulary and claims no
novelty for any individual mechanism. References to regulatory concepts in the
associated standardization use case are conceptual mappings only and do not
assert alignment with any regulatory framework.

## 7. Intended use

Reproducible, credential-free evidence for a **standardization use case**
discussion: that a runtime evidence gate with non-monotonic re-evaluation can
be expressed in a small, inspectable, independently runnable reference.
