# How VIDS is Governed

VIDS is maintained by a Steering Committee at Princeton Medical Systems. This page describes how decisions are made, who makes them, and where each decision is recorded.

VIDS uses lightweight governance. The goal is clear authority, technical integrity, openness, and traceability, without administrative process beyond demonstrated need. The full governance policy is [GOVERNANCE.md](https://github.com/vids-standard/vids-standard/blob/main/GOVERNANCE.md) in the repository; this page summarises it.

!!! quote "Normative authority"
    The VIDS Specification and its normative extensions are the only sources of VIDS conformance requirements.

Guides, examples, this website, validator messages, decision records, and other project materials may explain or support the Specification, but they do not independently create conformance requirements. If supporting material conflicts with the Specification, the Specification governs.

## Five principles

1. The Specification defines conformance.
2. The validator implements the Specification.
3. GitHub is the primary record of changes and approvals.
4. Routine work requires routine process.
5. Additional review is reserved for changes that materially affect adopters or VIDS governance.

## The validator does not define the standard

The validator implements machine-checkable requirements from the Specification. If the validator and the Specification appear to disagree, the Specification governs, the discrepancy is reviewed, and the validator or Specification is corrected as appropriate. A validator defect does not by itself change the meaning of an existing VIDS requirement. This principle was first recorded in [MD-0001](decision-records.md) and is now carried in the governance policy itself.

## Who decides what

Changes are graded, and the grade sets the process.

| Change | Process |
|--------|---------|
| **Editorial and routine**: typos, formatting, broken links, documentation improvements, examples that do not alter requirements | Merged by a maintainer. No separate approval record |
| **Substantive specification changes**: backward-compatible changes that affect the meaning or implementation of a requirement | Review by at least one other Steering Committee member before merge. The approving pull request is the decision record |
| **Major or breaking changes**: new REQUIRED information, removed requirements, material changes of meaning, incompatible structure changes | Public proposal, a minimum 30-day comment period, consideration of material feedback, and approval by at least two eligible Steering Committee members |

Decisions concerning governance, Steering Committee membership, or other significant policy matters require approval from at least two eligible Steering Committee members. Unanimous consent is not required. Routine technical and editorial decisions are not escalated to a Steering Committee vote.

## Steering Committee

| Member | Role |
|--------|------|
| Dr. Joan S. Muthu | Co-Founder and CTO |
| John Xavier | Co-Founder and Head of US and Global Operations |
| John Shalen R. | Co-Founder and COO |

The Steering Committee maintains the Specification, the validator, and related infrastructure; reviews substantive changes; approves major or breaking changes; makes governance and policy decisions; manages its own membership; and protects the neutrality and integrity of VIDS.

A member does not approve a decision where a material conflict of interest makes independent participation inappropriate. A recused member is excluded from that specific decision, and the resolution is documented in the relevant GitHub discussion or Maintainer Decision.

An **[Advisory Council](advisory-council.md)** of independent experts advises on strategy, clinical relevance and adoption. The Council is advisory: it does not define VIDS conformance and does not exercise Steering Committee authority. Members serve as individuals rather than as representatives of their employers. Appointments are approved by the Steering Committee under the normal decision rule.

## How a decision is recorded

GitHub is the primary project record: commits, pull requests, reviews, issues, releases, tags, and CI results. A change is proposed as a pull request, reviewed at the level its grade requires, and merged. The merged pull request and the repository history are the approval record. No signatures, approval certificates, or separate status registers are used.

A **Maintainer Decision (MD)** is written when a durable governance or policy decision is worth recording independently: a governance change, an important interpretation of authority, a major publication policy. An MD states the decision, the reason, and its effective point, and is accepted when the required Steering Committee approval is recorded and the corresponding pull request is merged. Decisions are append-only: a later decision that reverses or refines an earlier one is a new decision, and the earlier one is marked superseded.

## Project and commercial separation

VIDS governance covers the VIDS standard, its normative extensions, the open-source implementation, and associated governance decisions. It does not govern the ordinary internal operations of Princeton Medical Systems or any other company, and commercial activity does not independently redefine VIDS conformance.

## Where the records live

Everything normative and every governance decision is public in the [repository](https://github.com/vids-standard/vids-standard). The [Decision Records](decision-records.md) page lists each decision with its status and date, and links to the record itself.

## Amending this model

The governance policy may be amended with approval from at least two eligible Steering Committee members, proposed through a pull request that explains the reason for the change. Once merged, the updated GOVERNANCE.md is the current policy. Adoption of the current model is recorded in [MD-0008](decision-records.md), which superseded the earlier document-taxonomy operating model.
