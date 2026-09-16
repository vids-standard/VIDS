# Participation

VIDS is an open standard. The specification, the validator, every governance decision and every change note are public, and the routes below are the ways to take part.

## Report something

Issues are the preferred channel for anything technical: a validator that behaves incorrectly, a specification passage that is ambiguous, a worked example that does not do what it claims.

[Open an issue](https://github.com/vids-standard/vids-standard/issues)

A useful report says which version of the validator you ran, what you expected, and what happened. If a rule fired that you believe should not have, the rule identifier is the fastest thing to include.

## Propose a change

Changes to the standard are graded, and the grade sets the process.

| Change | Process |
|--------|---------|
| **Editorial**: typos, clarifications, better examples | Pull request. Merged by a maintainer |
| **Substantive**: backward-compatible changes that affect the meaning or implementation of a requirement, such as new optional fields, modality codes, annotation suffixes | Pull request describing the conformance impact. Review by at least one other Steering Committee member before merge |
| **Major or breaking**: new required fields, removed requirements, anything breaking | Public discussion first, minimum 30-day comment period, then approval by at least two eligible Steering Committee members |

If a pull request changes the specification, say whether the change is normative, meaning it affects conformance, or editorial. That single line determines which path the change takes.

Existing VIDS 1.x datasets remain conformant under later VIDS 1.x specifications, unless the earlier result depended on a validator defect or under-enforcement of an existing requirement. Breaking specification changes require a major version and an appropriate migration path.

## Add modality or framework support

New modality codes and new framework integrations are welcome and follow the minor-change path. The specification's extension mechanism describes what a proposal needs to include.

An extension ships when a real adopter presents a dataset that requires it. Extensions built in advance of an adopter tend to encode guesses, and a standard that covers everything enforces nothing.

## Become a maintainer

Contributors who demonstrate sustained, high-quality work may be nominated as maintainers by any Steering Committee member. What counts: multiple accepted pull requests across the specification or the tools, constructive participation in change discussions, and a demonstrated grasp of the design principles. Nominations are decided by the Steering Committee under the decision rule in the [governance model](index.md).

## Where this is going

The long-term model is a VIDS Consortium with formal representation from academic institutions, clinical organisations and industry adopters. The transition begins once VIDS has active external maintainers and multiple independent implementations. Until then, governance is held by the Steering Committee and recorded in public, so that the model can be inspected before anyone has to rely on it.

An **[Advisory Council](advisory-council.md)** of independent experts advises on strategy, clinical relevance and adoption. The Council is advisory: it does not define VIDS conformance and does not exercise Steering Committee authority. Members serve as individuals rather than as representatives of their employers.

## Contact

**Issues**: [github.com/vids-standard/vids-standard/issues](https://github.com/vids-standard/vids-standard/issues) for anything technical.

**Email**: standards@vidsstandard.org for partnership or governance enquiries.

## Licence

The specification and documentation are published under CC BY 4.0. The tools are published under Apache 2.0. Both permit commercial use.
