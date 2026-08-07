# Published Benchmark

In 2026 we scored four widely used public medical imaging datasets against the VIDS documentation model and published the result. This page records what was measured, how, and where to check it.

The analysis is published as a preprint, and the per-dimension scores are in a public repository so anyone can recompute them.

> Muthu, J. S. and Shalen, J. *VIDS: A Verified Imaging Dataset Standard for Medical AI.* arXiv:2604.17525.

## The finding

| Dataset | Documentation coverage |
|---|---|
| BraTS | 39% |
| MSD | 30% |
| LIDC-IDRI | 27% |
| CheXpert | 20% |

Four widely used public datasets document between a fifth and two fifths of what VIDS describes.

Provenance is the weakest category by a wide margin, averaging 0.38 out of 5 across the four. That is the category covering who made an annotation, with what tool, when, and under what review. It is also the category a downstream reader most needs when deciding whether to trust a label.

The point is not that these datasets are poor. They are established, actively maintained and widely cited, which is why they were chosen: they are a demanding rather than a forgiving test of the claim that documentation is thin. What the scores show is the size of the gap between what these datasets record and what VIDS asks for.

## Methodology

Each dataset was scored across 22 dimensions in six categories: Structure, Imaging, Annotation, Provenance, Quality and ML Readiness. Scoring is three-valued:

| Score | Meaning |
|---|---|
| **1.0** | Satisfied |
| **0.5** | Partial |
| **0.0** | Absent |

Partial credit has a precise definition, quoted from the published methodology:

> Information is present in the dataset but not in a machine-readable or standardized form (e.g., provenance described in a companion paper but absent from the dataset files).

That distinction is the reason for the middle value. A dataset that describes its annotation process in an accompanying paper has done something real, and something materially different from a dataset that documents nothing. It has also not done the thing VIDS asks for, which is to put that information where a machine can find it. Collapsing the two would erase exactly the distinction the standard exists to draw.

## Reproducing it

The per-dimension scores are published as JSON with a verification script.

```bash
git clone https://github.com/vids-standard/vids-benchmarks
cd vids-benchmarks
python verify_scores.py
```

The script computes the category and dataset totals from the per-dimension data rather than restating them, so a disagreement with the published figures would surface as a failure rather than a mismatch nobody notices.

[VIDS benchmarks repository](https://github.com/vids-standard/vids-benchmarks){target="_blank" rel="noopener"}

## How this relates to conformance

!!! warning "Benchmark scores are not conformance results"
    Benchmark scores describe documentation coverage. The validator determines conformance. Where they appear to disagree, the validator governs.

The benchmark was applied by hand, to datasets that predate VIDS and were never structured for it. That is what it is for: assessing a dataset that has never heard of the standard. The [Reference Validator](validator/index.md) does something different and narrower. It runs against a dataset already in VIDS form and returns PASS or FAIL against 21 rules, reproducibly, from any installation.

A benchmark percentage is a description. A validator result is a verdict. Only the second is a conformance claim, and only the specification defines what conformance means.

## The same methodology assesses a single dataset

Princeton Medical Systems applies these dimensions and this scale in [dataset documentation assessments](for-buyers/documentation-assessment.md), to one dataset rather than four. It is the same instrument, so an assessment score and a percentage on this page describe the same thing and can be read side by side.

There is no second scoring methodology. The specification defines the requirements, the validator determines conformance, and this methodology measures documentation coverage for datasets that were never structured for VIDS in the first place.
