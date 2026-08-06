# What VIDS Checks

VIDS verifies that a dataset's documentation is present and structured. That sentence is the boundary of the standard, and this page states exactly what falls inside it and what does not.

## The check

A dataset is validated against a profile. The reference validator applies 21 rules and reports PASS, FAIL, WARN or SKIP for each. A dataset is conformant if it has zero FAIL rules.

| Group | Rules | What is checked |
|-------|-------|-----------------|
| Structure | S001 to S006 | The profile marker, dataset description with its required fields, participants file, README, and at least one subject with at least one session |
| Imaging | I001 to I004 | An imaging file and its sidecar per subject, sidecars parse as JSON, and file naming follows the convention |
| Annotation | A001 to A005 | The annotations directory, at least one annotation across the five defined suffixes, binary annotations paired with sidecars, sidecars valid and carrying a version, and provenance fields populated |
| Quality | Q001 to Q003 | The quality directory, the quality summary, and the annotation agreement record. Full profile only |
| Machine learning | M001 to M002 | The splits directory and the splits file. Full profile only |
| Metadata | D001 | A changes file. Recommended, not required |

The [full rule list](https://github.com/vids-standard/vids-standard/blob/main/VALIDATION_RULES.md) gives each rule in detail.

## What a PASS means

A PASS asserts that the dataset satisfies the machine-checkable requirements of the selected profile.

It does not assert that:

- the image data are clinically correct;
- the annotations are clinically accurate;
- the annotator credentials are independently verified;
- extension fields are semantically validated beyond their documented structure;
- reported quality metrics, including Dice scores and pass rates, are independently recomputed or plausible.

This is the same boundary mature imaging standards draw. A validator can check that required elements are present and syntactically valid. It cannot prove that every supplied value is clinically correct or semantically true.

## Why the boundary is drawn there

A standard that promised more than it can check would be worth less, not more.

VIDS does not certify datasets. It does not attest to them, approve them, or provide assurance about them. That is not modesty about the tooling; it is a governance rule, recorded in MD-0006, and it binds the specification text, the worked examples, the generator output and the validator output alike. No VIDS artifact may make an outcome claim about a dataset unless a governance decision expressly authorises it, and no such decision exists.

One consequence follows directly and is worth stating, because it surprises people. A dataset whose documentation is present and correctly structured but thinly populated will pass. That is by design. VIDS tells a reader that the documentation exists and is where it should be. Whether the documentation is *good* is a judgement for the reader, and the standard makes that judgement possible rather than making it on the reader's behalf.

## How the check is kept honest

Naming a document "specification" does not keep it true. The tie between the standard and the tooling has to be mechanical, and this is what currently runs.

Continuous integration runs on every change to the repository, across three Python versions. It generates test fixtures, runs the validator against both profile examples, and runs the test suite. A failing test fails the build.

The suite includes tests that enforce governance rules directly rather than describing them. One set checks that the scaffolding generator emits no certification field and no date for an act it did not perform. Another checks that the repository holds no artifact that cannot be reviewed as a diff.

Two further checks are intended and not yet built: one tying rule counts and descriptions in the documentation to the validator, and one confirming that every enforced requirement names a real rule. Until they exist, those particular claims are checked by review rather than by machine, and the [governance model](index.md) says so on its face rather than implying otherwise.

## Profiles

**POC** is the entry profile: structure, imaging, and annotation with provenance.

**Full** adds quality documentation and machine-learning splits.

Both are defined in the [specification](https://github.com/vids-standard/vids-standard/blob/main/SPEC.md), which is the only document that creates a requirement.
