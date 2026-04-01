---
hide:
  - navigation
  - toc
---

<div class="vids-hero" markdown>

# VIDS — Verified Imaging Dataset Standard

<p class="vids-tagline">
An open standard for organizing, validating, and delivering annotated medical imaging datasets for AI/ML development. Structure · Provenance · Quality.
</p>

<div class="vids-badges">
  <a href="https://pypi.org/project/vids-validator/"><img src="https://img.shields.io/pypi/v/vids-validator?label=validator&color=3F51B5" alt="PyPI"></a>
  <a href="https://github.com/vids-standard/vids-standard"><img src="https://img.shields.io/github/stars/vids-standard/vids-standard?style=flat&color=3F51B5" alt="GitHub"></a>
  <a href="https://creativecommons.org/licenses/by/4.0/"><img src="https://img.shields.io/badge/spec-CC%20BY%204.0-3F51B5" alt="License"></a>
  <img src="https://img.shields.io/badge/version-1.0-3F51B5" alt="Spec v1.0">
</div>

</div>

<div class="vids-cards" markdown>

<div class="vids-card" markdown>

### :material-shield-check: Mandatory Provenance

Every annotation carries a structured record of who created it, when, with what tool, and under what quality controls. Provenance is a validation requirement, not a recommendation.

</div>

<div class="vids-card" markdown>

### :material-check-decagram: Automated Validation

21 rules. One command. Binary PASS/FAIL. Compliance is determined by running the validator — not by reading a checklist.

</div>

<div class="vids-card" markdown>

### :material-export: Framework Export

Curate once in VIDS, export to nnU-Net, MONAI, COCO JSON, or flat NIfTI. Provenance travels with the data through every format conversion.

</div>

</div>

---

## Quick Start

Install the validator and check any dataset in seconds:

```bash
pip install vids-validator
```

```bash
vids-validate /path/to/dataset
```

```bash
vids-validate /path/to/dataset --profile full --json
```

??? example "Example validator output"

    ```
    ============================================================
    VIDS Validation Report
    Profile: POC
    Dataset: /data/lung-nodule-ct-100
    ============================================================

      ✅ S001: .vids marker file present
      ✅ S002: dataset_description.json valid
      ✅ S003: Participants file present (json)
      ✅ S004: README.md present
      ✅ S005: 100 subject directories found
      ✅ S006: All subjects have session directories
      ✅ I001: All subjects have imaging files
      ✅ I002: All subjects have imaging sidecar JSONs
      ✅ I003: 100 imaging JSONs valid
      ✅ I004: All files follow VIDS naming convention
      ✅ A001: derivatives/annotations/ exists
      ✅ A002: 100 segmentation files found
      ✅ A003: 100 annotation sidecar JSONs found
      ✅ A004: 100 annotation JSONs valid
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

## What a VIDS Dataset Looks Like

```text
lung-nodule-ct-100/
├── .vids                              # Profile marker (poc or full)
├── dataset_description.json           # Dataset metadata
├── participants.json                  # Subject registry
├── README.md                          # Human-readable description
│
├── sub-001/
│   └── ses-baseline/
│       └── ct/
│           ├── sub-001_ses-baseline_ct_img.nii.gz
│           └── sub-001_ses-baseline_ct_img.json
│
├── derivatives/
│   └── annotations/
│       └── sub-001/
│           └── ses-baseline/
│               └── ct/
│                   ├── sub-001_ses-baseline_ct_seg.nii.gz
│                   └── sub-001_ses-baseline_ct_seg.json    ← provenance lives here
│
├── quality/                           # Full profile only
│   ├── quality_summary.json
│   └── annotation_agreement.json
│
└── ml/                                # Full profile only
    └── splits.json
```

Every annotation sidecar carries structured provenance:

```json
{
  "VIDSVersion": "1.0",
  "AnnotationType": "segmentation",
  "SourceImage": "sub-001_ses-baseline_ct_img.nii.gz",
  "Provenance": {
    "Annotator": {
      "ID": "radiologist_001",
      "Name": "Dr. Jane Smith",
      "Credentials": "MD, Board-certified radiologist, 10 years experience",
      "Specialty": "Chest Radiology"
    },
    "AnnotationProcess": {
      "Tool": "3D Slicer",
      "ToolVersion": "5.6.2",
      "Date": "2026-02-12",
      "TimeSpent_minutes": 15,
      "Method": "Manual segmentation"
    },
    "QualityControl": {
      "ReviewedBy": "senior_radiologist_001",
      "ReviewDate": "2026-02-13",
      "ReviewOutcome": "approved",
      "Confidence": 0.93
    }
  }
}
```

---

## Why VIDS?

Medical imaging datasets used to train AI models typically lack structured, machine-readable provenance. Annotation methodology exists in journal papers, README files, or institutional memory — invisible to any automated compliance or audit process.

Three converging pressures are making this untenable:

| Pressure | Problem | What VIDS Provides |
|----------|---------|-------------------|
| **Dataset duplication** | Datasets are copied across platforms without attribution or provenance | Every file carries its own structured metadata |
| **Synthetic data** | AI-generated images are indistinguishable from real scans | Origin documentation is a structural requirement |
| **Regulatory mandates** | EU AI Act, FDA, CDSCO require training data transparency | Machine-readable, auditable provenance chain |

---

## How VIDS Compares

VIDS is complementary to existing standards — it fills the gap none of them cover.

| | DICOM | BIDS | NIfTI | nnU-Net / MONAI | **VIDS** |
|---|---|---|---|---|---|
| Image storage | :material-check: | | :material-check: | | |
| Neuro folder structure | | :material-check: | | | |
| Multi-modality datasets | :material-check: | | | | :material-check: |
| Annotation provenance | | | | | :material-check: |
| Quality documentation | | | | | :material-check: |
| Automated validation | | :material-check:{ .partial } | | | :material-check: |
| ML framework export | | | | :material-check: | :material-check: |
| Compliance profiles | | | | | :material-check: |

---

## Citation

<div class="vids-cite" markdown>

```bibtex
@misc{vids2026,
  title   = {VIDS: Verified Imaging Dataset Standard, Specification v1.0},
  author  = {{Princeton Medical Systems}},
  year    = {2026},
  version = {1.0},
  url     = {https://vidsstandard.org/spec/1.0}
}
```

</div>

---

<div style="text-align: center; padding: 2rem 0 1rem;" markdown>

**VIDS is an open standard.**
Specification: [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) · Tools: [Apache 2.0](https://www.apache.org/licenses/LICENSE-2.0)

[:material-github: GitHub](https://github.com/vids-standard/vids-standard){ .md-button }
[:material-language-python: PyPI](https://pypi.org/project/vids-validator/){ .md-button }
[:material-file-document: Full Specification](specification/index.md){ .md-button .md-button--primary }

</div>
