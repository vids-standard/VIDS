# Documentation Scoring Rubric

The 22-dimension framework used in [dataset documentation assessments](documentation-assessment.md). It is a diagnostic instrument, not a conformance test. Published openly so that any score in any assessment report is traceable to documented criteria.

## Purpose

Publishing the criteria makes an assessment inspectable: a reader can see which dimension was scored, why, and disagree with a specific line rather than with a number. Several dimensions still call for judgement, so two reviewers may reach different conclusions on the same dataset; the rubric makes those differences visible and arguable rather than hidden. It complements the [VIDS Reference Validator](https://github.com/vids-standard/vids-standard){target="_blank" rel="noopener"} without replacing it, and the validator remains the only thing that determines conformance.

## Relationship to the validator

**VIDS conformance is determined by the Reference Validator, and by nothing else.** The validator checks 21 rules at the selected profile and produces the PASS or FAIL result. A rubric score is not a conformance result and cannot substitute for one.

The rubric is a diagnostic instrument. It scores 22 dimensions to describe how completely a dataset is documented, including some recommended items, such as class-distribution documentation, that the specification does not make a requirement. That breadth is useful for deciding what to fix; it is not a second definition of conformance.

| Validator (21 rules) | Rubric (22 dimensions) |
|---|---|
| Determines VIDS conformance: PASS or FAIL at the profile | Describes documentation coverage: X / 22 |
| Automated, reproducible from any installation | Assessed by a reviewer |
| Used in contract acceptance, see [validation reports](validation-report.md) | Used in [assessment reports](documentation-assessment.md) to explain gaps |
| Output: `validation_report.json` | Output: a written assessment |

Where the two appear to disagree, the validator governs. A dataset can hold a low rubric score and still be conformant, and a high score establishes nothing about conformance on its own.

## Scoring model

Each dimension is scored binary:

- **1** — Present and compliant. The pass criterion is fully met.
- **0** — Missing, non-compliant, or partially met. No partial credit.

No partial credit. A dimension either meets the pass criterion or it does not. This is deliberate: subjective half-credit scoring breaks reproducibility across evaluators.

### Reading a score

The score is reported as X / 22, with the missing dimensions named. There is no threshold, because the rubric does not issue a verdict. A dataset scoring 18 / 22 is not thereby "failing"; it is a dataset with four documentation gaps, which the report identifies so they can be closed.

Whether the dataset conforms is answered by running the validator. That answer is binary, automated, and reproducible by anyone holding the dataset.

---

## A. Structure (5 dimensions)

Structural compliance: directory layout, naming, and dataset-level metadata.

### S1 — Directory Structure
Dataset root contains required directories (`sub-*`/`ses-*`/`<modality>`/) and matches the VIDS reference layout. `derivatives/annotations/` tree mirrors the source tree.

### S2 — File Naming
All files follow the `sub-<ID>_ses-<ID>_<modality>_<suffix>.<extension>` pattern. Naming is deterministic and consistent across all subjects.

### S3 — Dataset Description
`dataset_description.json` present at root with all required fields: `Name`, `VIDSVersion`, `DatasetVersion`, `License`, `Description`, `Authors`.

### S4 — Metadata Consistency
Required fields populated across all subjects, sessions, and annotation files. Participants registry (`.json` or `.tsv`) lists every subject directory.

### S5 — Version Declaration
`.vids` marker file present and correctly declares profile (POC or Full) and `vids_version` (1.0).

---

## B. Annotation Provenance (6 dimensions)

The category that distinguishes VIDS from other dataset standards. Every annotation must trace back to who, when, how, and under what review.

### P1 — Annotator Identity
Each annotation sidecar records annotator ID or name. Pseudonymized identifiers are acceptable if mapped consistently across the dataset.

### P2 — Annotator Role / Type
Each annotation declares whether the annotator is human, automated, or hybrid. Human annotators carry credentials or specialty when available.

### P3 — Annotation Timestamp
Each annotation records the date (or datetime) the annotation was performed.

### P4 — Annotation Tool
Each annotation records the tool and version used (for example, 3D Slicer 5.6.2, MD.ai, custom pipeline).

### P5 — Annotation Protocol
A defined annotation protocol or guideline document is referenced from `dataset_description.json` or README. The same protocol applies to all subjects unless explicitly varied.

### P6 — Multi-annotator Tracking
Where multiple annotators contributed, each finding is attributable to a specific annotator. Reviewer / second-annotator records appear in the `QualityControl` block where applicable.

---

## C. Quality Documentation (5 dimensions)

Required for Full profile. Documents how quality was measured, not whether it is good.

### Q1 — QA Process Defined
`quality/quality_summary.json` describes the QA process: review percentage, double-annotation rate, review method.

### Q2 — QA Results
Measured outputs are reported: pass rates on first submission, after revision, total revisions required.

### Q3 — Inter-annotator Agreement
`quality/annotation_agreement.json` present with method (for example, Dice), sample size, aggregate statistics, and per-subject results where applicable.

### Q4 — Validation Evidence
Validation report from the VIDS Reference Validator is included in the dataset archive and references the specific validator version used.

### Q5 — Class Distribution
`quality/class_distribution.json` (or equivalent) documents class frequencies, anatomical or clinical-score distributions, and any known imbalances. Recommended for Full profile and required for any dataset intended for ML training.

---

## D. ML Readiness (6 dimensions)

Whether the dataset is usable in an ML pipeline without further restructuring.

### M1 — Label Consistency
Annotation schema is uniform across all subjects. `LabelMap` (for segmentation) is consistent; bounding box / classification taxonomies do not vary mid-dataset.

### M2 — Format Compatibility
Files are in standard ML-ready formats: NIfTI for imaging, JSON for sidecars. Export paths to nnU-Net, MONAI, COCO, or flat NIfTI are documented or exportable via the reference tooling.

### M3 — Data Completeness
No critical files are missing. Every subject directory contains the imaging and annotation files declared in the manifest. Empty or stub files are flagged in the documentation.

### M4 — Intended Use Declared
`dataset_description.json` declares the dataset's intended use (training, validation, regulatory submission) in the `Description` or `DatasetType` field.

### M5 — Known Limitations
README or `dataset_description.json` explicitly documents known limitations: anonymized identifiers, missing demographics, modality biases, geographic source restrictions.

### M6 — Train / Test Separation
`ml/splits.json` present with subject-level splits (no slice-level or study-level splits that risk data leakage). Random seed and split strategy documented.

---

## What this rubric does not do

- **Assess clinical correctness of annotations.** The rubric checks documentation; it does not verify whether a segmentation is anatomically correct.
- **Replace domain-specific quality criteria.** Buyer-defined acceptance criteria (subject count, modality coverage, label accuracy) layer on top of the rubric, not within it.
- **Establish regulatory compliance.** The rubric records what documentation is present; it does not constitute or replace FDA, EU AI Act, or CDSCO processes.

## Who uses this rubric

The rubric is a Princeton Medical Systems methodology, informed by VIDS but not part of it. It is not a registered VIDS artifact and creates no conformance requirement. It is published under CC BY 4.0 so that anyone may apply it, inspect it, or disagree with it, and so that an assessment produced with it can be checked rather than taken on trust.

## Related

- [Dataset Documentation Assessment](documentation-assessment.md) — how the rubric is applied to a specific dataset
- [Validation Report](validation-report.md) — the validator output, reproducible by anyone holding the dataset
- [VIDS Specification](../specification/index.md) — the underlying technical standard
- [Reference Procurement Language](sow-addendum.md) — contract clauses that make validator results binding
