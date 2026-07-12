# VIDS Validation Rules (v1.0)

VIDS compliance is determined by running the reference validator.

A dataset is compliant if it has zero FAIL rules.

## Structure rules (S\*)

- S001: `.vids` marker exists.
- S002: `dataset_description.json` exists and includes required fields: `Name`, `VIDSVersion`, `DatasetVersion`, `License`, `Description`, `Authors`.
- S003: `participants.json` or `participants.tsv` exists.
- S004: `README.md` exists.
- S005: at least one `sub-*` directory exists.
- S006: each subject has at least one `ses-*` directory.

## Imaging rules (I\*)

- I001: imaging NIfTI exists per subject (`*_img.nii.gz` or `*_img.nii`).
- I002: imaging sidecar exists (`*_img.json`).
- I003: imaging sidecars are valid JSON.
- I004: naming convention check; non-conforming files are WARN in the validator.

## Annotation rules (A\*)

- A001: `derivatives/annotations/` exists.
- A002: at least one annotation file exists across the five spec-defined suffixes (`*_seg.nii.gz`/`*_seg.nii`, `*_cls.json`, `*_bbox.json`, `*_lm.json`, `*_roi.json`).
- A003: every `_seg` binary has its paired `*_seg.json`; JSON-only annotations (`_cls`/`_bbox`/`_lm`/`_roi`) are self-sidecared and satisfy this rule.
- A004: all annotation sidecars, across all annotation types, are valid JSON and include `VIDSVersion`.
- A005: provenance completeness on all annotation sidecars: annotator identity and tool/date recorded (minimums).

## Quality rules (Q\*) — Full only

- Q001: `quality/` exists.
- Q002: `quality/quality_summary.json` exists.
- Q003: `quality/annotation_agreement.json` exists.

## ML rules (M\*) — Full only

- M001: `ml/` exists.
- M002: `ml/splits.json` exists.

## Metadata rule (D\*)

- D001: `CHANGES.md` exists; missing is WARN (recommended).
