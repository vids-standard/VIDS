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
| **Editorial**: typos, clarifications, better examples | Pull request. Merged by any maintainer |
| **Minor**: new optional fields, modality codes, annotation suffixes | Public issue first, then Steering Committee consensus |
| **Major**: new required fields, new validation rules, anything breaking | Public issue, minimum thirty-day comment period, consensus with community feedback in view |

If a pull request changes the specification, say whether the change is normative, meaning it affects conformance, or editorial. That single line determines which path the change takes.

Datasets valid under VIDS 1.0 remain valid under all VIDS 1.x validators. Breaking changes require a major version increment, a documented migration path, and ninety days of deprecation notice.

## Add modality or framework support

New modality codes and new framework integrations are welcome and follow the minor-change path. The specification's extension mechanism describes what a proposal needs to include.

An extension ships when a real adopter presents a dataset that requires it. Extensions built in advance of an adopter tend to encode guesses, and a standard that covers everything enforces nothing.

## Become a maintainer

Contributors who demonstrate sustained, high-quality work may be nominated as maintainers by any Steering Committee member. What counts: multiple accepted pull requests across the specification or the tools, constructive participation in change discussions, and a demonstrated grasp of the design principles. Nominations are decided by Steering Committee consensus.

## Where this is going

The long-term model is a VIDS Consortium with formal representation from academic institutions, clinical organisations and industry adopters. The transition begins once VIDS has active external maintainers and multiple independent implementations. Until then, governance is held by the Steering Committee and recorded in public, so that the model can be inspected before anyone has to rely on it.

An **Advisory Council** of independent experts advises on strategy, clinical relevance and adoption. The Council holds no normative vote, and its members serve as individuals rather than as representatives of their employers.

## Contact

**Issues**: [github.com/vids-standard/vids-standard/issues](https://github.com/vids-standard/vids-standard/issues) for anything technical.

**Email**: standards@vidsstandard.org for partnership or governance enquiries.

## Licence

The specification and documentation are published under CC BY 4.0. The tools are published under Apache 2.0. Both permit commercial use.
