# Validation Report

The Validation Report is the machine-readable output of the VIDS Reference Validator. It is the artifact a vendor delivers alongside a dataset, and the artifact a buyer reproduces independently before accepting delivery.

It is not a certificate, and VIDS does not issue one. The report records what the validator found. Its value is that anyone holding the dataset can regenerate it and get the same answer.

## What the report contains

Running the validator against a dataset produces a JSON report with the following fields.

| Field | Meaning |
|---|---|
| `VIDSVersion` | The specification version the dataset declares |
| `ValidatorVersion` | The exact validator build that produced this report |
| `DatasetPath` | The dataset the validator was run against |
| `Profile` | POC or Full |
| `ValidationDate` | When the validator ran, as a UTC timestamp |
| `Summary` | Rule counts and the overall PASS or FAIL |
| `Results` | One entry per rule: identifier, status, and message |
| `Errors` and `Warnings` | Collected FAIL and WARN messages, empty on a clean run |

A dataset conforms when it has zero FAIL rules at the selected profile. POC applies 15 rules; Full applies 21.

## Sample output

```json
{
  "VIDSVersion": "1.0",
  "ValidatorVersion": "1.2.1",
  "DatasetPath": "lidc-hybrid-100",
  "Profile": "full",
  "ValidationDate": "2026-06-12T09:14:03Z",
  "Summary": {
    "TotalRules": 21,
    "Passed": 21,
    "Failed": 0,
    "Warnings": 0,
    "Skipped": 0,
    "Status": "PASS"
  },
  "Results": [
    { "rule": "S001", "status": "PASS", "message": ".vids marker file present" },
    { "rule": "S002", "status": "PASS", "message": "dataset_description.json present and valid" }
  ],
  "Errors": [],
  "Warnings": []
}
```

`Results` is abbreviated here. A real report carries one entry for each of the 21 rules at either profile. Under POC, six of those entries are reported as SKIP.

This is the result for the [LIDC-Hybrid-100 reference dataset](https://doi.org/10.5281/zenodo.19582717){target="_blank" rel="noopener"}, which is publicly available. You can reproduce it yourself:

```bash
pip install vids-validator
vids-validate lidc-hybrid-100 --profile full --json
```

That reproducibility is the point. A claim you can check is worth more than a claim you are asked to accept.

## What a PASS does and does not tell you

A PASS states that the dataset satisfies the machine-checkable requirements of the selected profile: the structure is present, the required metadata files exist and parse, annotations carry provenance fields, and quality documentation is present where the profile requires it.

It does not state that:

- the image data are clinically correct;
- the annotations are clinically accurate;
- the annotator credentials have been independently verified;
- the reported quality metrics have been recomputed or found plausible.

VIDS verifies that documentation is present and structured. Whether the documentation is *good* remains a judgement for the reader. The standard exists to make that judgement possible, not to make it on the reader's behalf.

One consequence follows directly, and it is worth stating because it surprises people: a dataset whose documentation is present and correctly structured but thinly populated will pass. That is by design.

## How buyers use it

Under the [Reference Procurement Language](sow-addendum.md), acceptance is defined by the report and by the buyer's own re-run, not by any statement the vendor makes about the dataset.

1. Receive the dataset and the vendor's Validation Report.
2. Re-run the Reference Validator on the delivered dataset yourself.
3. Compare. If your result matches the vendor's report, the delivery meets the acceptance criterion.
4. If it differs, treat it as a failed validation and trigger the remediation clause.

Step 2 is not optional diligence. It is the mechanism. A report you did not generate tells you what someone else's tool said.

## When a result stops applying

A report describes one dataset version, validated on one date, with one validator build. It ceases to describe the dataset if:

- the dataset is modified in any way, including metadata-only changes;
- a later specification version introduces requirements the dataset has not been checked against;
- a validator defect is found that would have changed the original result.

In each case, re-run the validator. Regenerating a report costs nothing, which is another reason the report rather than a signed document is the right artifact.

## Related

- [Reference Procurement Language](sow-addendum.md) — contract clauses that make a validator result the acceptance condition
- [Dataset Documentation Assessment](documentation-assessment.md) — diagnostic review that identifies documentation gaps beyond validator conformance
- [Assessment Methodology](assessment-methodology.md) — the published 22 dimensions used in documentation assessments
- [VIDS Reference Validator](https://github.com/vids-standard/vids-standard){target="_blank" rel="noopener"} — the open-source tool, free to run
