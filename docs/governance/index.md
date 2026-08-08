# How VIDS is Governed

VIDS is maintained by a Steering Committee at Princeton Medical Systems. This page describes how decisions are made, who makes them, and where each decision is recorded.

The governing rule of the whole model is a single sentence.

!!! quote "The Normative Principle"
    Only the Core Specification (SPEC) creates, modifies, or removes dataset-conformance requirements.

Everything else in the model exists to make that principle unambiguous. A decision record, a change note, an operating procedure or a registry can explain, decide, or track. None of them can make a dataset conformant or non-conformant. Only the specification does that.

## Two layers

The repository holds two categories of document, and the dependency runs one way so that nothing has to define itself.

**Charter documents** define how the project operates: the governance model, the contribution rules, the licence. They are amended by Steering Committee consensus.

**Project artifacts** are what the project produces under that model, classified by the taxonomy below.

## The artifact taxonomy

| Code | Name | Purpose | Creates requirements? |
|------|------|---------|----------------------|
| **SPEC** | Specification | The normative standard: requirements, rules, schemas | **Yes** |
| **MD** | Maintainer Decision | A governance decision and its rationale | No |
| **CN** | Change Note | What changed, and what it means for adopters | No |
| **SOP** | Standard Operating Procedure | How the project operates internally | No |
| **REG** | Registry | Machine-readable inventory maintained by tooling | No |

Two distinctions are worth stating plainly, because they are where standards usually blur.

**A decision record is not a requirement.** A Maintainer Decision records what the maintainers decided and why. If that decision leads to a change in the standard, the change is made in the specification, through the specification's own review path. The decision record explains; the specification governs.

**A registry is not a backdoor.** Registries are authoritative for identifiers and traceability, and for nothing else. A registry records which requirement exists and how it traces to a validation rule. It cannot create the requirement.

## Who decides what

| Document type | Authored by | Accepted by |
|---------------|-------------|-------------|
| Charter documents | Anyone, by pull request | Steering Committee consensus |
| Specification | Contributors, by pull request | Maintainer ratification |
| Maintainer Decision | Anyone, as Proposed | Steering Committee acceptance |
| Change Note | Operations | Accuracy-gated |
| Registry | Tooling | Continuous integration, where implemented |

Specification changes are graded, and the grade sets the process. Editorial corrections can be merged by any maintainer. Minor additions require a public issue and Steering Committee consensus. Breaking changes require a public issue, a minimum thirty-day comment period, and consensus reached with community feedback in view.

## Steering Committee

| Member | Role |
|--------|------|
| Dr. Joan S. Muthu | Co-Founder and CTO |
| John Shalen R. | Co-Founder and COO |
| John Xavier | Co-Founder and Head of US and Global Operations |

All members hold governance signatory authority. Composition is recorded by Maintainer Decision and changes only by a subsequent decision taking effect from its stated date. It is recorded in [MD-0005](decision-records.md), not asserted on this page, so that there is one place to read it and one place to change it.

An **Advisory Council** of independent experts advises on strategy, clinical relevance and adoption. The Council holds no normative vote, and its members serve as individuals rather than as representatives of their employers.

## How a decision is recorded

Every Maintainer Decision follows the same lifecycle, and the reason for its shape is that a governance record should be checkable rather than asserted.

A decision is drafted as **Proposed**. A signature copy with blank sign-off blocks collects approvals. The signed document is filed as immutable approval evidence, held outside the public repository and cited by filename only. The published record then carries a Proposed date, an Accepted date, and a completed approval table. The Accepted date is the date the last required signature was given. It is never backdated.

Decisions are **append-only**. An accepted decision is not rewritten to change its meaning. A later decision that reverses or refines it is a new decision, and the earlier one is marked superseded. Correcting a factual error in a decision's description of the world is permitted and dated; changing the decision itself requires a new decision.

## Where the records live

Everything normative and every governance decision is public in the [repository](https://github.com/vids-standard/vids-standard). The [Decision Records](decision-records.md) page lists each decision with its status and date, and links to the record itself.

Internal operating procedures are not published. They describe how the project runs rather than what the standard requires, and nothing in them can create a conformance requirement.

## Amending this model

The governance model is itself a charter document, amended by Steering Committee consensus following the same review discipline as a specification change. Its adoption is recorded in MD-0002.
