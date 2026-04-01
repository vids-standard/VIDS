# Quick Start

Validate your first dataset in 2 minutes.

---

## 1. Check a dataset (auto-detect profile)

The validator reads the `.vids` marker file to determine whether to apply POC or Full rules:

```bash
vids-validate /path/to/my-dataset
```

Output:

```
============================================================
VIDS Validation Report
Profile: POC
Dataset: /path/to/my-dataset
============================================================

  ✅ S001: .vids marker file present
  ✅ S002: dataset_description.json valid
  ✅ S003: Participants file present (json)
  ✅ S004: README.md present
  ✅ S005: 10 subject directories found
  ✅ S006: All subjects have session directories
  ✅ I001: All subjects have imaging files
  ✅ I002: All subjects have imaging sidecar JSONs
  ✅ I003: 10 imaging JSONs valid
  ✅ I004: All files follow VIDS naming convention
  ✅ A001: derivatives/annotations/ exists
  ✅ A002: 10 segmentation files found
  ✅ A003: 10 annotation sidecar JSONs found
  ✅ A004: 10 annotation JSONs valid
  ✅ A005: All annotations have complete provenance
  ⏭  Q001: POC profile — quality/ optional
  ⏭  Q002: POC profile — quality_summary optional
  ⏭  Q003: POC profile — annotation_agreement optional
  ⏭  M001: POC profile — ml/ optional
  ⏭  M002: POC profile — splits optional
  ⚠️  D001: CHANGES.md missing (recommended)

------------------------------------------------------------
  Passed:   15
  Failed:   0
  Warnings: 1
  Skipped:  5
------------------------------------------------------------

✅ VALIDATION PASSED (15/21 rules)
```

---

## 2. Validate with Full profile

```bash
vids-validate /path/to/my-dataset --profile full
```

Full profile enforces all 21 rules, including quality documentation (`quality/`) and ML splits (`ml/`).

---

## 3. Get JSON output

For programmatic use or CI pipelines:

```bash
vids-validate /path/to/my-dataset --json
```

```json
{
  "VIDSVersion": "1.0",
  "ValidatorVersion": "1.1",
  "DatasetPath": "/path/to/my-dataset",
  "Profile": "poc",
  "ValidationDate": "2026-04-01T10:30:00Z",
  "Summary": {
    "TotalRules": 21,
    "Passed": 15,
    "Failed": 0,
    "Warnings": 1,
    "Skipped": 5,
    "Status": "PASS"
  },
  "Results": [ ... ],
  "Errors": [],
  "Warnings": ["D001: CHANGES.md missing (recommended)"]
}
```

---

## 4. Save report to file

```bash
vids-validate /path/to/my-dataset --output report.json
```

This writes the JSON report to `report.json` and prints the human-readable summary to the console.

---

## 5. Use in Python

```python
from vids_validator import VIDSValidator

validator = VIDSValidator("/path/to/my-dataset", profile="auto")
report = validator.validate()

if report["Summary"]["Status"] == "PASS":
    print("Dataset is VIDS-compliant!")
else:
    for error in report["Errors"]:
        print(f"  ❌ {error}")
```

---

## 6. Use in CI/CD

The validator exits with code `0` on PASS and `1` on FAIL, making it suitable for CI pipelines:

```yaml
# GitHub Actions example
- name: Validate VIDS compliance
  run: |
    pip install vids-validator
    vids-validate ./my-dataset --profile poc
```

---

## Understanding the Output

Each of the 21 rules produces one of four outcomes:

| Status | Meaning |
|--------|---------|
| ✅ **PASS** | Rule satisfied |
| ❌ **FAIL** | Rule violated — dataset is non-compliant |
| ⚠️ **WARN** | Recommended practice not followed — does not block compliance |
| ⏭ **SKIP** | Rule not applicable to the declared profile |

A dataset is **VIDS-compliant** if and only if zero rules have FAIL status.

---

## What If Validation Fails?

Common failures and fixes:

| Rule | Common Cause | Fix |
|------|-------------|-----|
| S001 | Missing `.vids` file | Create a `.vids` file with `profile: poc` and `vids_version: 1.0` |
| S002 | Missing fields in `dataset_description.json` | Add all 6 required fields: `Name`, `VIDSVersion`, `DatasetVersion`, `License`, `Description`, `Authors` |
| A005 | Incomplete provenance in annotation sidecars | Ensure every `_seg.json` has `Provenance.Annotator.ID` (or `.Name`) and `Provenance.AnnotationProcess.Date` (or `.Tool`) |

See [Validation Rules](../specification/validation-rules.md) for the complete rule reference.
