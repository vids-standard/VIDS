# Decision Records

Every governance decision made about VIDS is recorded, numbered, and public. This page is the index. Each record is held in the repository and linked below.

Two kinds of record appear here.

A **Maintainer Decision (MD)** answers *what did we decide, and why*. It is forward-looking and append-only.

A **Change Note (CN)** answers *what changed, and what does it mean for adopters*. It is backward-looking and immutable once published.

Neither creates a conformance requirement. Only the [Specification](https://github.com/vids-standard/vids-standard/blob/main/SPEC.md) does that.

## Maintainer Decisions

| ID | Title | Status | Accepted |
|----|-------|--------|----------|
| [MD-0001](https://github.com/vids-standard/vids-standard/blob/main/governance/MD-0001.md) | Authority of the Specification over the Validator | Accepted | 2026-07-26 |
| [MD-0002](https://github.com/vids-standard/vids-standard/blob/main/governance/MD-0002.md) | Adoption of the VIDS Document Taxonomy | Accepted | 2026-07-26 |
| [MD-0003](https://github.com/vids-standard/vids-standard/blob/main/governance/MD-0003.md) | Reference-Implementation Publication Policy | Accepted | 2026-07-26 |
| [MD-0004](https://github.com/vids-standard/vids-standard/blob/main/governance/MD-0004.md) | Adoption of the VIDS Governance Handbook v1.0 | Accepted | 2026-07-26 |
| [MD-0005](https://github.com/vids-standard/vids-standard/blob/main/governance/MD-0005.md) | Steering Committee Composition and Signatory Authority | Accepted | 2026-07-28 |
| [MD-0006](https://github.com/vids-standard/vids-standard/blob/main/governance/MD-0006.md) | Assertion Discipline for VIDS Artifacts and Generators | Accepted | 2026-07-31 |
| [MD-0007](https://github.com/vids-standard/vids-standard/blob/main/governance/MD-0007.md) | DeIdentification Semantics in SPEC Section 8.2 | Accepted | 2026-07-31 |
| [MD-0008](https://github.com/vids-standard/vids-standard/blob/main/governance/MD-0008.md) | Adoption of the Simplified Governance Model | Accepted | 2026-09-10 |

## Change Notes

| ID | Title | Status |
|----|-------|--------|
| [CN-0001](https://github.com/vids-standard/vids-standard/blob/main/governance/CN-0001.md) | Validator v1.2.x Annotation-Sidecar Enforcement | Published |

## What some of these decided

A few of these records answer questions adopters ask, so they are worth summarising here. The record itself is authoritative in each case.

**MD-0001** settles what happens when the validator and the specification disagree. The specification wins. A validator that enforces something the specification does not require has a defect in the validator.

**MD-0003** sets what a reference implementation publishes. VIDS reference datasets publish the metadata layer: the documentation, provenance and structure that VIDS describes. They do not republish source images.

**MD-0006** records a rule about what VIDS artifacts and tools may claim. No VIDS document, schema field, generator output or validator output may assert that a dataset is certified, attested, approved or assured, unless a governance decision expressly authorises that claim. No such authorisation exists. It also records that a tool may fill in a provenance field only when the act that field describes is the act the tool just performed.

That second rule has a practical consequence. The scaffolding generator now writes placeholders rather than dates for acts it did not carry out, such as de-identification or annotation. A placeholder is the honest value.

**MD-0008** adopts the simplified governance model now in force. GitHub records proposals, reviews, approvals, and merges; the prior signature and register mechanics are retired. It supersedes the operating model adopted in MD-0002; the earlier records stand unchanged as accepted historical records.

**MD-0007** applies the same discipline to one field. Upstream de-identification and downstream format conversion are separate acts, recorded in separate fields. A format converter is not a de-identification tool, even where converting a file incidentally drops header information.

## Errata

Corrections to released normative text are recorded inside the specification itself, dated, at the point of the correction. They are not separate documents. Superseded wording is preserved alongside the correction rather than deleted, so that a reader can see what the text used to say and why it changed.
