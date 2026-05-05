# VIDS Compliance Scoring Rubric

The 22-dimension framework used to score medical imaging datasets in [VIDS Compliance Evaluations](evaluation.md). Published openly so that any score in any evaluation report is traceable to documented criteria.

## Purpose

The rubric makes evaluations consistent across operators, defensible against scrutiny, and reproducible from the same dataset inputs. It complements the [VIDS Reference Validator](https://github.com/vids-standard/vids-standard){target="_blank" rel="noopener"} without replacing it.

## Relationship to the validator

The VIDS Reference Validator checks 21 rules and produces a binary PASS/FAIL outcome. The rubric scores 22 dimensions and produces a granular score (X / 22) used for diagnostic detail. The two scoring systems serve different purposes:

| Validator (21 rules) | Rubric (22 dimensions) |
|---|---|
| Binary PASS/FAIL at the specified Profile | Granular scoring (X / 22) for diagnostic detail |
| Used in: contract acceptance, [attestation](attestation.md) issuance | Used in: [evaluation reports](evaluation.md), public benchmarks |
| Automated, reproducible from any installation | Manual scoring by trained evaluator |
| Output: `validation_report.json` | Output: VIDS Compliance Evaluation Report |

The rubric is wider than the validator by design. It covers some recommended fields (such as class distribution documentation) that are not yet hard-validated rules but still inform a buyer's judgment. Validator results take precedence for contract decisions; rubric scores supply the explanation.

## Scoring model

Each dimension is scored binary:

- **1** — Present and compliant. The pass criterion is fully met.
- **0** — Missing, non-compliant, or partially met. No partial credit.

No partial credit. A dimension either meets the pass criterion or it does not. This is deliberate: subjective half-credit scoring breaks reproducibility across evaluators.

### Profile thresholds

| Profile | Required | Notes |
|---|---|---|
| **POC** | 16 / 22 | All Structure (S1–S5) and all Provenance (P1–P6) dimensions must be present (5 + 6 = 11 mandatory). Quality and ML Readiness dimensions add to the count but are individually optional. Threshold = mandatory 11 + 5 of remaining 11. |
| **Full** | 22 / 22 | All 22 dimensions must score 1. A single missing dimension = FAIL. This aligns with the validator's zero-FAIL requirement at the Full profile. |

PASS / FAIL is the headline outcome. The X / 22 score exists to explain what failed, not to create a "this is mostly compliant" soft pass. There is no soft pass.

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
- **Certify regulatory compliance.** The rubric provides auditable evidence; it does not constitute or replace FDA, EU AI Act, or CDSCO certification.

## Operator

The current operator of VIDS Compliance Evaluations using this rubric is Princeton Medical Systems. The rubric itself is part of the VIDS open standard and is governed under the same license terms (CC BY 4.0).

## Related

- [Compliance Evaluation](evaluation.md) — how the rubric is applied to a specific dataset
- [Validation Attestation](attestation.md) — issued for datasets that achieve 22 / 22 at the Full profile
- [VIDS Specification](../specification/index.md) — the underlying technical standard
- [Reference Procurement Language](sow-addendum.md) — contract clauses that make validator results binding
